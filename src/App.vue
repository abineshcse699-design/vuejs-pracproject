<script setup>
import AppNavbar from '@/components/Navbar/AppNavbar.vue'
import TgCard1 from '@/components/TG/TgCard1.vue'
import LeftSidebar from '@/components/lay/LeftSidebar.vue'
import SubjectRightSection from '@/components/lay/SubjectRightSection.vue'
import OnePageTable from './components/one page table.vue'
import ApplicationsTable from '@/components/table/ApplicationsTable.vue'
  // ✅ Uncommented
import BadgePage from '@/components/BadgePage.vue'
import V from '@/components/v.vue'
</script>

<template>
  <AppNavbar />

  <TgCard1 />

  <!-- MAIN LAYOUT WRAPPER -->
  <div class="main-layout">
    <LeftSidebar class="sidebar" />
    <SubjectRightSection class="content" />
  </div>

  <OnePageTable />
  <ApplicationsTable />

  <!-- Alert Section -->
  <div style="padding:20px;">
    <Alert title="Alert Example" variant="warning">
      This is an alert message.
    </Alert>
  </div>

  <!-- Badge Section -->
  <div class="badge-section">
    <h2>Badge</h2>

    <div class="badge-row">
      <BadgePage label="Default" variant="default" size="small" />
      <BadgePage label="Success" variant="success" size="small" />
      <BadgePage label="Info" variant="info" size="small" />
      <BadgePage label="Warning" variant="warning" size="small" />
      <BadgePage label="Medium" variant="success" size="medium" />
    </div>
  </div>
  <V></V>
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

/* Badge Section */
.badge-section {
  padding: 20px;
}

.badge-row {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  margin-top: 12px;
}

/* 📱 TABLET & MOBILE */
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