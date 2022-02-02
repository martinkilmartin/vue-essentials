<script setup>
import { ref } from 'vue'

const message = ref('Hi Earthlings!')
</script>

<template>
  <h1>{{ message.split('').reverse().join('') }}</h1>
</template>