<script setup lang="ts">
import AppCard from '@/components/table/AppCard.vue'
import AppTable from '@/components/table/AppTable.vue'

const rows = [
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
</script>

<template>
  <div class="page">
    <AppCard title="DataTable">
      <AppTable :rows="rows" />

      <template #footer>
        Sort: { "key": "", "direction": null } | Selected:
      </template>
    </AppCard>
  </div>
</template>

<style scoped>
.page {
  background: #f3f4f6;
  padding: 40px;
  font-family: 'Figtree', sans-serif;
}
</style>