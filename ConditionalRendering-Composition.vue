<script setup>
import { ref } from "vue";

const show = ref(true);

function toggle() {
  show.value = !show.value;
}
</script>

<template>
  <div>
    <button @click="toggle">toggle</button>
    <h1 v-if="show">Sionnach Solutions is awesome! 🦊</h1>
    <h1 v-else>Sionnach Buí is even more awesome! 🦊🐈</h1>
  </div>
</template>