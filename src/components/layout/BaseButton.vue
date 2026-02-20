<template>
  <button
    class="px-4 py-2 rounded-full bg-green-700 text-white hover:bg-green-800 transition"
    @click="$emit('click')"
  >
    <slot />
  </button>
</template>
