<template>
  <button
    class="bg-green-700 hover:bg-green-800 text-white px-5 py-2 rounded-full text-sm font-semibold transition"
    @click="$emit('click')"
  >
    <slot></slot>
  </button>
</template>

<script setup>
defineEmits(['click'])
</script>
