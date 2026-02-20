<script  setup>
import { ref } from 'vue'

const newTask = ref("")

function formSubmitted() {
  console.log("New Task:", newTask.value)
  newTask.value = ""
}
</script>

<template>
  <form @submit.prevent="formSubmitted">
    <label>
      New Task
      <input v-model="newTask" name="newTask" />
    </label>

    <div class="button-container">
      <button>Add</button>
    </div>
  </form>
</template>
