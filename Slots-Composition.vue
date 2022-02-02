<!-- AlienComponent.vue
<template>
  <slot>The truth is out there</slot>
</template>
-->
<script setup>
import { ref } from "vue";
import AlienChild from "./AlienComponent.vue";

const msg = ref("👽");
</script>

<template>
  <AlienChild>{{ msg }}</AlienChild>
</template>