<script setup>
import { ref } from "vue";

const text = ref("");
</script>

<template>
  <div>
    <input v-model="text" placeholder="Enter text" />
    <p>{{ text }}</p>
  </div>
</template>