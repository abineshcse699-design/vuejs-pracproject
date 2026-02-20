<template>
  <header class="w-full">

    <!-- TOP NAVBAR -->
    <div class="bg-[#1f3b37] text-white">
      <div class="max-w-7xl mx-auto px-8 py-4 flex justify-between items-center">

        <!-- BRAND -->
        <div class="text-3xl font-bold tracking-widest">
          <span v-if="!loading">{{ navbar.brand }}</span>
          <span v-else class="animate-pulse">Loading...</span>
        </div>

        <!-- MENU -->
        <ul class="flex items-center gap-8 text-sm font-semibold relative">

          <li
            v-for="menu in navbar.menus"
            :key="menu.id"
            class="relative"
          >
            <!-- Menu Label -->
            <div
              @click="toggleDropdown(menu)"
              class="flex items-center gap-1 cursor-pointer hover:text-yellow-400 transition"
            >
              {{ menu.label }}
              <span
                v-if="menu.hasDropdown"
                class="text-yellow-400 text-xs"
              >
                ▼
              </span>
            </div>

            <!-- DROPDOWN -->
            <div
              v-if="activeDropdown === menu.id"
              class="absolute top-full left-0 mt-3 bg-white text-black rounded-lg shadow-xl w-48 py-2 z-50"
            >
              <div
                v-for="(item, index) in menu.dropdown"
                :key="index"
                class="px-4 py-2 hover:bg-gray-100 cursor-pointer"
              >
                {{ item }}
              </div>
            </div>

          </li>

          <!-- SEARCH ICON -->
          <li class="cursor-pointer text-lg hover:text-yellow-400">
            🔍
          </li>

        </ul>
      </div>
    </div>

    <!-- BREADCRUMB -->
    <div class="bg-[#cddc00]">
      <div class="max-w-7xl mx-auto px-8 py-3 text-sm font-medium text-[#1f3b37]">
        <span
          v-for="(item, index) in breadcrumb"
          :key="index"
        >
          <span :class="{ 'font-bold': index === breadcrumb.length - 1 }">
            {{ item }}
          </span>
          <span v-if="index !== breadcrumb.length - 1"> / </span>
        </span>
      </div>
    </div>

  </header>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const navbar = ref({
  brand: '',
  menus: []
})

const breadcrumb = ref([])
const loading = ref(false)
const activeDropdown = ref(null)

/* Toggle Dropdown */
const toggleDropdown = (menu) => {
  if (!menu.hasDropdown) return

  if (activeDropdown.value === menu.id) {
    activeDropdown.value = null
  } else {
    activeDropdown.value = menu.id
  }
}

/* Close dropdown when clicking outside */
const handleClickOutside = (event) => {
  if (!event.target.closest('li')) {
    activeDropdown.value = null
  }
  
}

const fetchNavbar = async () => {
  loading.value = true
  try {
    const navRes = await fetch('http://localhost:3001/navbar')
    if (!navRes.ok) throw new Error('Navbar fetch failed')
    navbar.value = await navRes.json()

    const breadRes = await fetch('http://localhost:3001/breadcrumb')
    if (!breadRes.ok) throw new Error('Breadcrumb fetch failed')
    breadcrumb.value = await breadRes.json()

  } catch (error) {
    console.error(error)
  } finally {
    loading.value = false
  }
}

onMounted(() => {
  fetchNavbar()
  document.addEventListener('click', handleClickOutside)
})

onBeforeUnmount(() => {
  document.removeEventListener('click', handleClickOutside)
})
</script>
