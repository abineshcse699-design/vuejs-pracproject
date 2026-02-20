<template>
  <CardSection class="bg-white border border-gray-200 rounded-md shadow-sm">
    <template #header>{{ title }}

    </template>

    <p class="p-4 border-b border-gray-200">
      {{ price }}
    </p>

    <p class="p-4">
      {{ description }}
    </p>
  </CardSection>
</template>

<script setup>
import RoundedCard from '@/components/compo/RoundedCard.vue';
import CardSection from '@/components/compo/CardSection.vue';

defineProps({
  title: String,
  price: Number,
  description: String,
})
</script>
