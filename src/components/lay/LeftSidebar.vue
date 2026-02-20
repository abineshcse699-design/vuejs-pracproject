<template>
  <div class="sidebar">

    <h3 class="title">Chapters</h3>

    <SidebarItem
      v-for="chapter in chapters"
      :key="chapter.id"
      :number="chapter.number"
      :title="chapter.title"
      :active="chapter.active"
    />

    <div class="collapse">
      ← Collapse
    </div>

  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import SidebarItem from '@/components/lay/SidebarItem.vue'

const chapters = ref([])

onMounted(async () => {
  const res = await fetch('http://localhost:3001/chapters')
  chapters.value = await res.json()
})
</script>

<style scoped>
.sidebar {
  width: 200px;
  background: #f5f7f6;
  padding: 24px 18px;
  border-right: 1px solid #e2e2e2;
  height: 115vh;
}

.title {
  font-size: 16px;
  margin-bottom: 22px;
  font-weight: 600;
}

.collapse {
  margin-top: 20px;
  font-size: 14px;
  cursor: pointer;
  color: #555;
}
</style>
