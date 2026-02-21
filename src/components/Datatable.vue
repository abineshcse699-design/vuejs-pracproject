<script setup lang="ts">
import { computed } from 'vue'

export type SortDirection = 'asc' | 'desc' | null

export interface DataTableColumn {
  key: string
  label: string
  sortable?: boolean
}

export interface DataTableSortState {
  key: string
  direction: SortDirection
}

const props = withDefaults(defineProps<{
  columns: DataTableColumn[]
  rows: Record<string, any>[]
  rowKey?: string
  selectable?: boolean
  selectedRowKeys?: (string | number)[]
  sortState?: DataTableSortState
}>(), {
  rowKey: 'id',
  selectable: false,
  selectedRowKeys: () => [],
})

const emit = defineEmits<{
  (e: 'update:selectedRowKeys', keys: (string | number)[]): void
  (e: 'sort', state: DataTableSortState): void
}>()

const isAllSelected = computed(() =>
  props.rows.length > 0 &&
  props.selectedRowKeys.length === props.rows.length
)

const allKeys = computed(() =>
  props.rows.map(r => r[props.rowKey!])
)

function toggleSelectAll() {
  if (isAllSelected.value) {
    emit('update:selectedRowKeys', [])
  } else {
    emit('update:selectedRowKeys', [...allKeys.value])
  }
}

function toggleRow(key: string | number) {
  const exists = props.selectedRowKeys.includes(key)

  if (exists) {
    emit('update:selectedRowKeys',
      props.selectedRowKeys.filter(k => k !== key)
    )
  } else {
    emit('update:selectedRowKeys',
      [...props.selectedRowKeys, key]
    )
  }
}

function onSort(column: DataTableColumn) {
  if (!column.sortable) return

  let direction: SortDirection = 'asc'

  if (props.sortState?.key === column.key) {
    direction =
      props.sortState.direction === 'asc'
        ? 'desc'
        : 'asc'
  }

  emit('sort', { key: column.key, direction })
}
</script>

<template>
  <div class="table-card">
    <div class="table-title">
      DataTable (Multi-Select + Filters)
    </div>

    <table>
      <thead>
        <tr>
          <th v-if="selectable" class="checkbox-cell">
            <input
              type="checkbox"
              :checked="isAllSelected"
              @change="toggleSelectAll"
            />
          </th>

          <th
            v-for="col in columns"
            :key="col.key"
            @click="onSort(col)"
            :class="{ sortable: col.sortable }"
          >
            <span class="header-content">
              {{ col.label }}
              <span class="icons">
                <span v-if="col.sortable">
                  {{ sortState?.key === col.key
                      ? sortState.direction === 'asc'
                        ? '↑'
                        : '↓'
                      : '↕' }}
                </span>
                <span class="filter-icon">⛃</span>
              </span>
            </span>
          </th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="row in rows" :key="row[rowKey]">
          <td v-if="selectable" class="checkbox-cell">
            <input
              type="checkbox"
              :checked="selectedRowKeys.includes(row[rowKey])"
              @change.stop="toggleRow(row[rowKey])"
            />
          </td>

          <td v-for="col in columns" :key="col.key">
            {{ row[col.key] }}
          </td>
        </tr>
      </tbody>
    </table>

    <div class="selected-info">
      Selected: {{ selectedRowKeys }}
    </div>
  </div>
</template>

<style scoped>
.table-card {
  background: #f8f8f8;
  padding: 20px;
  border-radius: 12px;
  border: 1px solid #e5e5e5;
}

.table-title {
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 16px;
}

table {
  width: 100%;
  border-collapse: collapse;
  background: white;
  border-radius: 8px;
  overflow: hidden;
}

thead {
  background: #f3f3f3;
}

th, td {
  padding: 14px;
  border-bottom: 1px solid #eaeaea;
  font-size: 14px;
  text-align: left;
}

th.sortable {
  cursor: pointer;
}

.header-content {
  display: flex;
  align-items: center;
  gap: 6px;
}

.icons {
  display: flex;
  gap: 6px;
  font-size: 12px;
  color: #999;
}

.filter-icon {
  font-size: 12px;
}

.checkbox-cell {
  width: 40px;
}

tbody tr:hover {
  background: #fafafa;
}

.selected-info {
  margin-top: 12px;
  font-size: 14px;
}
</style>