<template>
  <input
    v-model="model"
    type="text"
    class="border border-gray-300 rounded-md px-4 py-2 focus:ring-2 focus:ring-green-600 outline-none"
  />
</template>

<script setup>
const model = defineModel()
</script>
