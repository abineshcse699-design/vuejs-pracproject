
<script setup>
import AppNavbar from '@/components/Navbar/AppNavbar.vue'
import TgCard1 from '@/components/TG/TgCard1.vue'
import LeftSidebar from '@/components/lay/LeftSidebar.vue'
import SubjectRightSection from '@/components/lay/SubjectRightSection.vue'
</script>

<template>
  <AppNavbar />

  <TgCard1 />

  <!-- MAIN LAYOUT WRAPPER adc-->
  <div class="main-layout">

    <LeftSidebar />

    <SubjectRightSection />

  </div>
</template>

<style scoped>
.main-layout {
  display: flex;
  align-items: flex-start;
}

/* LEFT SIDEBAR FIX WIDTH */
.main-layout > :first-child {
  width: 200px;
  flex-shrink: 0;
  height: 115vh;
}

/* RIGHT SECTION TAKE REMAINING SPACE */
.main-layout > :last-child {
  flex: 1;
}
</style>
