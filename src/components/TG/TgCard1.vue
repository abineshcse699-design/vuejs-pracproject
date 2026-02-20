<template>
<section class="p-6 bg-gray-100 w-[100%]">


    <div
      v-for="tg in tgCards"
      :key="tg.id"
     class="bg-white border border-gray-200 w-[87%] rounded-xl shadow-sm overflow-hidden ml-24"

    >

      <!-- TOP SECTION -->
      <div class="px-8 py-6 flex justify-between items-start">

        <!-- LEFT SIDE -->
        <div class="flex gap-20">

          <!-- Main Common Name -->
          <div>
            <p class="text-sm text-gray-500">
              Main Common Name(s):
            </p>
            <p class="text-xl font-semibold text-green-900">
              {{ tg.mainName }}
            </p>
          </div>

          <!-- UPOV Codes -->
          <div>
            <p class="text-sm text-gray-500 ml-22">
              UPOV Code(s):
            </p>
  <p class="text-xl font-semibold text-green-900 ml-22">


              {{ tg.upovCodes.join('; ') }}
            </p>
          </div>

        </div>

        <!-- Submit Button -->
        <button
          @click="submitCard(tg.id)"
          class="bg-green-700 hover:bg-green-800 text-white font-medium px-6 py-2 rounded-full"
        >
          Submit
        </button>

      </div>

      <!-- ONLY ONE DIVIDER (Like Image 2) -->
      <div class="border-t border-gray-200"></div>

      <!-- FOOTER -->
      <div class="px-8 py-5 flex justify-between items-center">

        <!-- Left -->
        <div class="flex items-center gap-2 text-gray-700 cursor-pointer">
          <span>▾</span>
          <span>More details</span>
        </div>

        <!-- Right -->
        <div class="text-right">
          <div class="font-semibold text-gray-900">
            {{ tg.tgCode }}
          </div>
          <div class="text-gray-500">
            Saved: {{ tg.savedFrom }} - {{ tg.savedTo }}
          </div>
        </div>

      </div>

    </div>

  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const tgCards = ref([])

const fetchCards = async () => {
  const res = await fetch('http://localhost:3001/tgcards')
  tgCards.value = await res.json()
}

const submitCard = (id) => {
  alert(`Submitted TG Card ID: ${id}`)
}

onMounted(fetchCards)
</script>
