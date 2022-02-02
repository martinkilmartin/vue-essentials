<script setup>
import { ref } from 'vue'

const count = ref(0)

function inc() {
  count.value++
}
</script>

<template>
  <button @click="inc">{{ count }}</button>
</template>