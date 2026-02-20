<template>
  <div class="min-h-screen bg-gray-100 flex">

    <!-- Sidebar -->
    <AppSidebar
      :chapters="chapters"
      :activeId="1"
    />

    <!-- Main Content -->
    <main class="flex-1 p-10">

      <h1 class="text-2xl font-semibold text-green-800 mb-6">
        1. {{ subjectData?.title }}
      </h1>

      <BaseCard v-if="subjectData" class="space-y-6">

        <p>
          These Test Guidelines apply to all varieties of
          <span class="italic">
            {{ subjectData.plantName }}
          </span>.
        </p>

        <div class="flex gap-6">
          <BaseRadio
            v-model="subjectData.clarification"
            value="yes"
            label="Yes"
          />
          <BaseRadio
            v-model="subjectData.clarification"
            value="no"
            label="No"
          />
        </div>

        <BaseInput v-model="subjectData.hybridText" />

        <BaseButton @click="saveData">
          Save
        </BaseButton>

      </BaseCard>

    </main>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import AppSidebar from '@/components/layout/AppSidebar.vue'
import BaseCard from '@/components/layout/BaseCard.vue'
import BaseRadio from '@/components/layout/BaseRadio.vue'
import BaseInput from '@/components/layout/BaseInput.vue'
import BaseButton from '@/components/layout/BaseButton.vue'

const chapters = ref([])
const subjectData = ref(null)

const fetchData = async () => {
  const res1 = await fetch('http://localhost:3001/chapters')
  chapters.value = await res1.json()

  const res2 = await fetch('http://localhost:3001/subjectPage')
  subjectData.value = await res2.json()
}

const saveData = async () => {
  await fetch('http://localhost:3001/subjectPage/1', {
    method: 'PUT',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(subjectData.value)
  })
  alert('Saved to DB')
}

onMounted(fetchData)
</script>
