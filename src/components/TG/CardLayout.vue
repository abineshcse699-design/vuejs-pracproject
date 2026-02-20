<template>
  <BaseCard>

    <!-- HEADER -->
    <div
      v-if="$slots.header"
      class="p-4 border-b border-gray-200"
    >
      <slot name="header"></slot>
    </div>

    <!-- BODY -->
    <div
      :class="{
        'p-4': true,
        'border-b border-gray-200': $slots.footer
      }"
    >
      <slot></slot>
    </div>

    <!-- FOOTER -->
    <div v-if="$slots.footer" class="p-4">
      <slot name="footer"></slot>
    </div>

  </BaseCard>
</template>

<script setup>
import BaseCard from '@/components/TG/Basecard.vue'
</script>
