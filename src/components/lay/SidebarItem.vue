<template>
  <div
    class="sidebar-item"
    :class="{ active: active }"
  >
    <div
      class="circle"
      :class="{ activeCircle: active }"
    >
      {{ number }}
    </div>

    <span class="label">
      {{ title }}
    </span>
  </div>
</template>

<script setup>
defineProps({
  number: String,
  title: String,
  active: Boolean
})
</script>

<style scoped>
.sidebar-item {
  display: flex;
  align-items: center;
  padding: 12px 16px;
  border-radius: 8px;
  margin-bottom: 10px;
  cursor: pointer;
  transition: all 0.2s ease;
  position: relative;
  width: 100%;              /* responsive width */
  max-width: 220px;
}

/* HOVER */
.sidebar-item:hover {
  background: #eef5f2;
}

/* ACTIVE BACKGROUND */
.sidebar-item.active {
  background: #dfeee8;
}

/* RIGHT GREEN BAR (auto height) */
.sidebar-item.active::after {
  content: "";
  position: absolute;
  right: 0;
  top: 8px;
  bottom: 8px;
  width: 4px;
  background: #1f7a5c;
  border-radius: 4px;
}

/* CIRCLE */
.circle {
  width: 34px;
  height: 34px;
  border-radius: 50%;
  border: 2px solid #c8c8c8;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 14px;
  font-weight: 600;
  color: #6b6b6b;
  transition: all 0.2s ease;
  flex-shrink: 0;
}

/* ACTIVE CIRCLE */
.activeCircle {
  background: #1f7a5c;
  color: white;
  border: none;
}

/* LABEL */
.label {
  font-size: 15px;
  color: #2c2c2c;
  transition: 0.2s ease;
  word-break: break-word;
}

/* ACTIVE TEXT */
.sidebar-item.active .label {
  color: #1f7a5c;
  font-weight: 600;
}

/* -------------------- */
/* 📱 MOBILE RESPONSIVE */
/* -------------------- */
@media (max-width: 768px) {

  .sidebar-item {
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 10px;
    margin-bottom: 0;
    max-width: none;
  }

  .circle {
    margin-right: 0;
    margin-bottom: 6px;
    width: 30px;
    height: 30px;
    font-size: 14px;
  }

  .label {
    font-size: 13px;
  }

  /* Active bar becomes bottom bar on mobile */
  .sidebar-item.active::after {
    top: auto;
    bottom: 0;
    left: 20%;
    right: 20%;
    height: 3px;
    width: auto;
  }
}
</style>