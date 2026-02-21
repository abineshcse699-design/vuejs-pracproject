<script setup lang="ts">
defineProps<{ label: string }>()
</script>

<template>
  <th>
    <div class="header-content">
      {{ label }}
      <span class="sort-icons">
        <span class="arrow up"></span>
        <span class="arrow down"></span>
      </span>
    </div>
  </th>
</template>

<style scoped>
th {
  padding: 14px 16px;
  text-align: left;
  font-weight: 600;
  color: #374151;
  white-space: nowrap;
}

.header-content {
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
</style>