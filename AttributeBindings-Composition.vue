<script setup>
import { ref } from 'vue'

const titleClass = ref('brand')
</script>

<template>
  <h1 :class="titleClass">Sionnach Solutions</h1>
</template>

<style>
.brand {
  color: red;
}
</style>