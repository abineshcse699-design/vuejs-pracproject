<script setup>
import AppNavbar from '@/components/Navbar/AppNavbar.vue'
import TgCard1 from '@/components/TG/TgCard1.vue'
import LeftSidebar from '@/components/lay/LeftSidebar.vue'
import SubjectRightSection from '@/components/lay/SubjectRightSection.vue'
</script>

<template>
  <AppNavbar />

  <TgCard1 />

  <!-- MAIN LAYOUT WRAPPER -->
  <div class="main-layout">

    <LeftSidebar class="sidebar" />

    <SubjectRightSection class="content" />

  </div>
</template>

<style scoped>
.main-layout {
  display: flex;
  align-items: flex-start;
  min-height: 100vh;
}

/* DESKTOP */
.sidebar {
  width: 220px;
  flex-shrink: 0;
}

.content {
  flex: 1;
  padding: 20px;
}

/* ----------------------- */
/* 📱 TABLET & MOBILE */
/* ----------------------- */
@media (max-width: 1024px) {
  .main-layout {
    flex-direction: column;
  }

  .sidebar {
    width: 100%;
    height: auto;
    border-bottom: 1px solid #e5e5e5;
  }

  .content {
    width: 100%;
    padding: 16px;
  }
}
</style>