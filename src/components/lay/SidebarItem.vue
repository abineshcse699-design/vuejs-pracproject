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
  width: 180px;
}

/* HOVER */
.sidebar-item:hover {
  background: #eef5f2;
}

/* ACTIVE BACKGROUND */
.sidebar-item.active {
  background: #dfeee8;
}

/* RIGHT GREEN BAR (FIXED PERFECT ALIGN) */
.sidebar-item.active::after {
  content: "";
  position: absolute;
  right: 0;
  top: 0px;        /* equal spacing top */
  bottom: 12px;     /* equal spacing bottom */
  width: 3px;
  background: #1f7a5c;
  border-radius: 8px;
  height: 60px;
  margin-right: -1px;
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
}

/* ACTIVE TEXT */
.sidebar-item.active .label {
  color: #1f7a5c;
  font-weight: 600;
}
</style>
