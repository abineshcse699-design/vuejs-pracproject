<script setup lang="ts">
import { computed } from 'vue'

interface Row {
  id: number
  reference: string
  application: string
  modified: string
  crop: string
  status: 'In progress' | 'Submitted' | 'Accepted'
}

const rows: Row[] = [
  {
    id: 1,
    reference: 'XU_3020250000010',
    application: 'PBR',
    modified: '10/12/2024',
    crop: 'Lactuca sativa L.',
    status: 'In progress'
  },
  {
    id: 2,
    reference: 'XU_3020250000095',
    application: 'National Listing (VL)',
    modified: '12/06/2024',
    crop: 'Solanum lycopersicum L.',
    status: 'Submitted'
  },
  {
    id: 3,
    reference: 'XU_3020250000154',
    application: 'PBR',
    modified: '08/06/2024',
    crop: 'Allium oschaninii',
    status: 'Accepted'
  },
  {
    id: 4,
    reference: 'XU_3020250000145',
    application: 'PBR',
    modified: '21/04/2024',
    crop: 'Cucumis melo L.',
    status: 'In progress'
  }
]

function badgeClass(status: string) {
  if (status === 'Submitted') return 'badge-blue'
  if (status === 'Accepted') return 'badge-green'
  return 'badge-orange'
}
</script>

<template>
  <div class="page">
    <div class="card">

      <!-- Header -->
      <div class="card-header">
        DataTable
      </div>

      <!-- Table -->
      <div class="table-wrapper">
        <table>
          <thead>
            <tr>
              <th>
                <div class="th-content">
                  International Reference Number
                  <span class="sort-icons">
                    <span class="arrow up"></span>
                    <span class="arrow down"></span>
                  </span>
                </div>
              </th>

              <th>
                <div class="th-content">
                  Application data for
                  <span class="sort-icons">
                    <span class="arrow up"></span>
                    <span class="arrow down"></span>
                  </span>
                </div>
              </th>

              <th>
                <div class="th-content">
                  Modified on
                  <span class="sort-icons">
                    <span class="arrow up"></span>
                    <span class="arrow down"></span>
                  </span>
                </div>
              </th>

              <th>
                <div class="th-content">
                  Crop
                  <span class="sort-icons">
                    <span class="arrow up"></span>
                    <span class="arrow down"></span>
                  </span>
                </div>
              </th>

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
                <span :class="['badge', badgeClass(row.status)]">
                  {{ row.status }}
                </span>
              </td>
              <td class="menu">⋮</td>
            </tr>
          </tbody>
        </table>
      </div>

      <!-- Footer -->
      <div class="card-footer">
        Sort: { "key": "", "direction": null } | Selected:
      </div>

    </div>
  </div>
</template>

<style scoped>
.page {
    width: 85%;
    margin-left: 7%;
  background: #f3f4f6;
  padding: 40px;
  font-family: 'Figtree', sans-serif;
}

.card {
  background: #ffffff;
  border: 1px solid #dcdcdc;
  border-radius: 8px;
  overflow: hidden;
}

/* Header */
.card-header {
  background: #f5f6f7;
  padding: 16px 20px;
  font-weight: 600;
  font-size: 16px;
  color: #1f2937;
}

/* Table */
.table-wrapper {
  padding: 0 20px;
}

table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
}

thead tr {
  border-bottom: 1px solid #e5e7eb;
}

th {
  padding: 14px 16px;
  text-align: left;
  font-weight: 600;
  color: #374151;
  white-space: nowrap;
}

td {
  padding: 14px 16px;
  color: #4b5563;
}

/* Horizontal lines */
tbody tr {
  border-bottom: 1px solid #f1f3f5;
}

tbody tr:last-child {
  border-bottom: none;
}

/* ONLY 2 Vertical lines like image */
th:nth-child(1),
td:nth-child(1) {
  border-right: 1px solid #e5e7eb;
}

th:nth-child(4),
td:nth-child(4) {
  border-right: 1px solid #e5e7eb;
}

/* Sort icons */
.th-content {
  display: flex;
  align-items: center;
  gap: 6px;
}

.sort-icons {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.arrow {
  width: 0;
  height: 0;
  border-left: 6px solid transparent;
  border-right: 6px solid transparent;
}

.arrow.up {
  border-bottom: 6px solid #9ca3af;
}

.arrow.down {
  border-top: 6px solid #9ca3af;
}

/* Reference link */
.reference {
  color: #047857;
  text-decoration: underline;
  text-decoration-color:goldenrod;
  text-decoration-thickness: 3px;
  font-weight: 500;
  cursor: pointer;
}

/* Badges */
.badge {
  padding: 4px 12px;
  border-radius: 16px;
  font-size: 12px;
  font-weight: 500;
}

.badge-orange {
  background: #fef3c7;
  color: #b45309;
}

.badge-blue {
  background: #dbeafe;
  color: #1d4ed8;
}

.badge-green {
  background: #d1fae5;
  color: #047857;
}

/* Menu */
.menu {
  text-align: center;
  font-size: 18px;
  color: #6b7280;
  cursor: pointer;
}

.menu:hover {
  color: #111827;
}

.menu-col {
  width: 40px;
}

/* Footer */
.card-footer {
  border-top: 1px solid #e5e7eb;
  padding: 12px 20px;
  font-size: 13px;
  color: #6b7280;
  background: #fafafa;
}
</style>