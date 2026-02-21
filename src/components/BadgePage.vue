<script setup lang="ts">
type Variant = 'success' | 'info' | 'warning' | 'default'
type Size = 'small' | 'medium'

const props = defineProps<{
  label?: string
  variant?: Variant
  size?: Size
}>()
</script>

<template>
  <span
    class="badge-atom"
    :class="[
      `badge-atom--${props.variant ?? 'success'}`,
      `badge-atom--${props.size ?? 'small'}`
    ]"
  >
    {{ props.label ?? 'Updated' }}
  </span>
</template>

<style scoped lang="scss">
.badge-atom {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 4px 6px;
  border-radius: 8px;
  font-family: 'Figtree', sans-serif;
  font-size: 12px;
  font-weight: 500;
  line-height: 16px;
  letter-spacing: 0.5px;
  height: 24px;
  border: 1px solid #ffffff;

  &--small {
    padding: 2px 8px;
  }

  &--medium {
    padding: 4px 12px;
  }

  &--success {
    background-color: #009a6e;
    color: #ffffff;
  }

  &--info {
    background-color: #d1ecf1;
    color: #0c5460;
  }

  &--warning {
    background-color: #fff3cd;
    color: #856404;
  }

  &--default {
    background-color: #009a6e;
    color: #ffffff;
  }
}
</style>