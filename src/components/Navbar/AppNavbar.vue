<template>
  <header class="w-full">

    <!-- TOP NAVBAR -->
    <div class="bg-[#1f3b37] text-white">
      <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">

        <!-- BRAND -->
        <div class="text-2xl md:text-3xl font-bold tracking-widest">
          <span v-if="!loading">{{ navbar.brand }}</span>
          <span v-else class="animate-pulse">Loading...</span>
        </div>

        <!-- HAMBURGER (Mobile Only) -->
        <button
          class="md:hidden text-2xl"
          @click="mobileMenuOpen = !mobileMenuOpen"
        >
          ☰
        </button>

        <!-- MENU (Desktop) -->
        <ul class="hidden md:flex items-center gap-8 text-sm font-semibold relative">

          <li
            v-for="menu in navbar.menus"
            :key="menu.id"
            class="relative"
          >
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

          <!-- SEARCH -->
          <li class="cursor-pointer text-lg hover:text-yellow-400">
            🔍
          </li>

        </ul>
      </div>

      <!-- MOBILE MENU -->
      <div
        v-if="mobileMenuOpen"
        class="md:hidden bg-[#244640] px-6 py-4 space-y-4"
      >
        <div
          v-for="menu in navbar.menus"
          :key="menu.id"
        >
          <div
            @click="toggleDropdown(menu)"
            class="flex justify-between items-center cursor-pointer py-2 font-semibold"
          >
            {{ menu.label }}
            <span v-if="menu.hasDropdown">▼</span>
          </div>

          <!-- Mobile Dropdown -->
          <div
            v-if="activeDropdown === menu.id"
            class="pl-4 mt-2 space-y-2 text-sm text-gray-200"
          >
            <div
              v-for="(item, index) in menu.dropdown"
              :key="index"
              class="cursor-pointer"
            >
              {{ item }}
            </div>
          </div>
        </div>

        <div class="text-lg pt-2 cursor-pointer">🔍 Search</div>
      </div>
    </div>

    <!-- BREADCRUMB -->
    <div class="bg-[#cddc00]">
      <div class="max-w-7xl mx-auto px-6 py-3 text-sm font-medium text-[#1f3b37] overflow-x-auto whitespace-nowrap">
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
const mobileMenuOpen = ref(false)

/* Toggle Dropdown */
const toggleDropdown = (menu) => {
  if (!menu.hasDropdown) return

  activeDropdown.value =
    activeDropdown.value === menu.id ? null : menu.id
}

/* Close dropdown when clicking outside */
const handleClickOutside = (event) => {
  if (!event.target.closest('header')) {
    activeDropdown.value = null
    mobileMenuOpen.value = false
  }
}

const fetchNavbar = async () => {
  loading.value = true
  try {
    const navRes = await fetch('http://localhost:3001/navbar')
    navbar.value = await navRes.json()

    const breadRes = await fetch('http://localhost:3001/breadcrumb')
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