<script setup lang="ts">
defineProps<{ title: string }>()
</script>

<template>
  <div class="app-card">
    <div class="app-card__header">
      {{ title }}
    </div>

    <div class="app-card__body">
      <slot />
    </div>

    <div class="app-card__footer">
      <slot name="footer" />
    </div>
  </div>
</template>

<style scoped>
.app-card {
  background: #fff;
  border: 1px solid #dcdcdc;
  border-radius: 8px;
  overflow: hidden;
}

.app-card__header {
  background: #f5f6f7;
  padding: 16px 20px;
  font-weight: 600;
  font-size: 16px;
  color: #1f2937;
}

.app-card__body {
  padding: 0 20px;
}

.app-card__footer {
  border-top: 1px solid #e5e7eb;
  padding: 12px 20px;
  font-size: 13px;
  color: #6b7280;
  background: #fafafa;
}
</style>