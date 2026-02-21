<script setup lang="ts">
import SortableHeader from '@/components/table/SortableHeader.vue'
import StatusPill from '@/components/table/StatusPill.vue'

interface Row {
  id: number
  reference: string
  application: string
  modified: string
  crop: string
  status: 'In progress' | 'Submitted' | 'Accepted'
}

defineProps<{ rows: Row[] }>()
</script>

<template>
  <table>
    <thead>
      <tr>
        <SortableHeader label="International Reference Number" />
        <SortableHeader label="Application data for" />
        <SortableHeader label="Modified on" />
        <SortableHeader label="Crop" />
        <th>Status</th>
        <th class="menu-col"></th>
      </tr>
    </thead>

    <tbody>
      <tr v-for="row in rows" :key="row.id">
        <td class="reference">{{ row.reference }}</td>
        <td>{{ row.application }}</td>
        <td>{{ row.modified }}</td>
        <td>{{ row.crop }}</td>
        <td>
          <StatusPill :status="row.status" />
        </td>
        <td class="menu">⋮</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
}

thead tr {
  border-bottom: 1px solid #e5e7eb;
}

tbody tr {
  border-bottom: 1px solid #f1f3f5;
}

tbody tr:last-child {
  border-bottom: none;
}

td {
  padding: 14px 16px;
  color: #4b5563;
}

.reference {
  color: #a3b600;
  text-decoration: underline;
  font-weight: 500;
  cursor: pointer;
}

th:nth-child(1),
td:nth-child(1) {
  border-right: 1px solid #e5e7eb;
}

th:nth-child(4),
td:nth-child(4) {
  border-right: 1px solid #e5e7eb;
}

.menu {
  text-align: center;
  font-size: 18px;
  color: #6b7280;
  cursor: pointer;
}

.menu-col {
  width: 40px;
}
</style>