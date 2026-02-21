<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{
  status: 'In progress' | 'Submitted' | 'Accepted'
}>()

const pillClass = computed(() => {
  if (props.status === 'Submitted') return 'pill-blue'
  if (props.status === 'Accepted') return 'pill-green'
  return 'pill-orange'
})
</script>

<template>
  <span :class="['pill', pillClass]">
    {{ status }}
  </span>
</template>

<style scoped>
.pill {
  padding: 4px 12px;
  border-radius: 16px;
  font-size: 12px;
  font-weight: 500;
}

.pill-orange {
  background: #fef3c7;
  color: #b45309;
}

.pill-blue {
  background: #dbeafe;
  color: #1d4ed8;
}

.pill-green {
  background: #d1fae5;
  color: #047857;
}
</style>