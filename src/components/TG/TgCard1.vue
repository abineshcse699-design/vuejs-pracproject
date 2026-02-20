<template>
<section class="p-4 md:p-6 bg-gray-100 w-full">

  <div
    v-for="tg in tgCards"
    :key="tg.id"
    class="bg-white border border-gray-200 rounded-xl shadow-sm overflow-hidden w-full max-w-6xl mx-auto mb-6"
  >

    <!-- TOP SECTION -->
    <div class="px-4 md:px-8 py-6 flex flex-col md:flex-row md:justify-between md:items-start gap-6">

      <!-- LEFT SIDE -->
      <div class="flex flex-col sm:flex-row gap-6 md:gap-16">

        <!-- Main Common Name -->
        <div>
          <p class="text-sm text-gray-500">
            Main Common Name(s):
          </p>
          <p class="text-lg md:text-xl font-semibold text-green-900">
            {{ tg.mainName }}
          </p>
        </div>

        <!-- UPOV Codes -->
        <div>
          <p class="text-sm text-gray-500">
            UPOV Code(s):
          </p>
          <p class="text-lg md:text-xl font-semibold text-green-900">
            {{ tg.upovCodes.join('; ') }}
          </p>
        </div>

      </div>

      <!-- Submit Button -->
      <button
        @click="submitCard(tg.id)"
        class="bg-green-700 hover:bg-green-800 text-white font-medium px-6 py-2 rounded-full self-start md:self-auto w-full sm:w-auto"
      >
        Submit
      </button>

    </div>

    <!-- DIVIDER -->
    <div class="border-t border-gray-200"></div>

    <!-- FOOTER -->
    <div class="px-4 md:px-8 py-5 flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4">

      <!-- Left -->
      <div class="flex items-center gap-2 text-gray-700 cursor-pointer">
        <span>▾</span>
        <span>More details</span>
      </div>

      <!-- Right -->
      <div class="text-left sm:text-right">
        <div class="font-semibold text-gray-900">
          {{ tg.tgCode }}
        </div>
        <div class="text-gray-500 text-sm">
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