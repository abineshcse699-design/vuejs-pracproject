<script setup lang="ts">
import { ref } from 'vue'
import DataTable, { DataTableColumn } from '@/components/Datatable.vue'

const columns: DataTableColumn[] = [
  { key: 'name', label: 'Name', sortable: true },
  { key: 'email', label: 'Email address', sortable: true },
  { key: 'company', label: 'Company' },
  { key: 'notes', label: 'Notes' }
]

const rows = ref([
  {
    id: 1,
    name: 'Hend Madhour',
    email: 'hend.madhour@upov.int',
    company: 'UPOV',
    notes: 'My fees are 100 USD per application'
  },
  {
    id: 2,
    name: 'Jose Ramon',
    email: 'joseramon@legalfirm.com',
    company: 'Legal firm',
    notes: ''
  },
  {
    id: 3,
    name: 'Ana Laura Thompson',
    email: 'analaurathompson@plantfirm.com',
    company: 'Plant free wind',
    notes: 'Lorem ipsum dolor sit amet'
  },
  {
    id: 4,
    name: 'Hend Madhour',
    email: 'hend.madhour@upov.int',
    company: 'UPOV',
    notes: 'My fees are 100 USD per application'
  },
  {
    id: 5,
    name: 'Jose Ramon',
    email: 'joseramon@legalfirm.com',
    company: 'Legal firm',
    notes: ''
  }
])

const selected = ref<(string | number)[]>([])
const sortState = ref({ key: '', direction: null })
</script>

<template>
  <DataTable
    :columns="columns"
    :rows="rows"
    selectable
    v-model:selectedRowKeys="selected"
    :sortState="sortState"
    @sort="val => sortState = val"
  />
</template>