<template>
  <aside class="w-72 bg-white border-r border-gray-200 p-6">
    <h2 class="text-lg font-semibold mb-6">Chapters</h2>

    <ul class="space-y-3">
      <ChapterItem
        v-for="chapter in chapters"
        :key="chapter.id"
        :chapter="chapter"
        :active="chapter.id === activeId"
        @click="$emit('change', chapter.id)"
      />
    </ul>
  </aside>
</template>

<script setup>
import ChapterItem from './ChapterItem.vue'

defineProps({
  chapters: Array,
  activeId: Number
})
</script>
