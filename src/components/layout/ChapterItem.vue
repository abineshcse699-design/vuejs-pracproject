<template>
  <li
    class="flex items-center gap-3 cursor-pointer"
    :class="active ? 'text-green-700 font-semibold' : 'text-gray-600'"
  >
    <div
      class="w-8 h-8 flex items-center justify-center rounded-full border"
      :class="active
        ? 'bg-green-100 border-green-600 text-green-700'
        : 'border-gray-300'"
    >
      {{ chapter.id.toString().padStart(2, '0') }}
    </div>

    <span>{{ chapter.name }}</span>
  </li>
</template>

<script setup>
defineProps({
  chapter: Object,
  active: Boolean
})
</script>
