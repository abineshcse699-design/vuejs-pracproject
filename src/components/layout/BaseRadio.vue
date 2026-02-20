<template>
  <label class="flex items-center gap-2 cursor-pointer">
    <input
      type="radio"
      :value="value"
      v-model="model"
      class="accent-green-700"
    />
    {{ label }}
  </label>
</template>

<script setup>
const model = defineModel()

defineProps({
  value: String,
  label: String
})
</script>
