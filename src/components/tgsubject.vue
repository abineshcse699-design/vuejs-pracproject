<template>
  <div class="min-h-screen bg-gray-100 flex">

    <!-- LEFT SIDEBAR -->
    <aside class="w-72 bg-white border-r border-gray-200 p-6">
      <h2 class="text-lg font-semibold mb-6">Chapters</h2>

      <ul class="space-y-3">
        <li
          v-for="chapter in chapters"
          :key="chapter.id"
          class="flex items-center gap-3 cursor-pointer"
          :class="chapter.id === 1 ? 'text-green-700 font-semibold' : 'text-gray-600'"
        >
          <div
            class="w-8 h-8 flex items-center justify-center rounded-full border"
            :class="chapter.id === 1
              ? 'bg-green-100 border-green-600 text-green-700'
              : 'border-gray-300'"
          >
            {{ chapter.id.toString().padStart(2, '0') }}
          </div>

          <span>{{ chapter.name }}</span>
        </li>
      </ul>

      <div class="mt-10 text-sm text-gray-500 cursor-pointer">
        ← Collapse
      </div>
    </aside>

    <!-- MAIN CONTENT -->
    <main class="flex-1 p-10">

      <h1 class="text-2xl font-semibold text-green-800 mb-6">
        1. Subject of these Test Guidelines
      </h1>

      <!-- CARD -->
      <div class="bg-white rounded-xl shadow-sm border border-gray-200 p-8 space-y-6">

        <!-- RELATED LINKS -->
        <div class="text-sm text-gray-600">
          <span class="font-medium">Related links:</span>
          <span class="ml-2 text-green-700 cursor-pointer hover:underline">
            More than one species (GN3)
          </span>
        </div>

        <!-- TEXT -->
        <p class="text-gray-700">
          These Test Guidelines apply to all varieties of
          <span class="italic">Malpighia emarginata</span> DC.
        </p>

        <!-- RADIO SECTION -->
        <div class="space-y-3">
          <p class="text-gray-700">
            Should clarification be provided that any other species or hybrids
            not explicitly covered by these Test Guidelines should be treated
            according to the provisions?
          </p>

          <div class="flex gap-6">
            <label class="flex items-center gap-2">
              <input type="radio" value="yes" v-model="clarification" />
              Yes
            </label>

            <label class="flex items-center gap-2">
              <input type="radio" value="no" v-model="clarification" />
              No
            </label>
          </div>
        </div>

        <!-- INPUT FIELD -->
        <div>
          <label class="block text-gray-700 mb-2">
            Guidance on the use of Test Guidelines for
          </label>

          <input
            v-model="hybridText"
            type="text"
            class="w-96 border border-gray-300 rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-green-600"
          />
        </div>

        <!-- ADD PARAGRAPH BUTTON -->
        <button
          class="border border-green-700 text-green-700 px-4 py-2 rounded-full hover:bg-green-50 transition"
        >
          + Add Paragraph
        </button>

        <!-- SECOND RADIO -->
        <div class="space-y-3">
          <p class="text-gray-700">
            Might it be necessary to add additional characteristics?
          </p>

          <div class="flex gap-6">
            <label class="flex items-center gap-2">
              <input type="radio" value="yes" v-model="additionalChar" />
              Yes
            </label>

            <label class="flex items-center gap-2">
              <input type="radio" value="no" v-model="additionalChar" />
              No
            </label>
          </div>
        </div>

      </div>

      <!-- PREVIEW BOX -->
      <div class="mt-8 bg-gray-100 border border-gray-300 rounded-lg p-6">
        <p class="text-sm font-medium text-gray-600 mb-2">
          PREVIEW
        </p>

        <p class="text-gray-800">
          1.1 These Test Guidelines apply to all varieties of
          Argania spinosa (L.) Skeels.
        </p>
      </div>

    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const clarification = ref('yes')
const additionalChar = ref('yes')
const hybridText = ref('interspec. hybrids')

const chapters = [
  { id: 1, name: 'Subject' },
  { id: 2, name: 'Material' },
  { id: 3, name: 'Examination' },
  { id: 4, name: 'Grouping' },
  { id: 5, name: 'Characteristics' },
  { id: 6, name: 'Characteristics' },
  { id: 7, name: 'Table of characteristics' },
  { id: 8, name: 'Explanations' },
  { id: 9, name: 'Literature' },
  { id: 10, name: 'Technical questionnaire' },
  { id: 11, name: 'Annex' },
]
</script>
