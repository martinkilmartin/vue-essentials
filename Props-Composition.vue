<!-- AlienComponent.vue
<script setup>
const props = defineProps({
  msg: String
})
</script>

<template>
  <h2>{{ msg || 'Mommy?' }}</h2>
</template>
-->
<script setup>
import { ref } from "vue";
import AlienChild from "./AlienComponent.vue";

const greeting = ref("Mommy loves you!");
</script>

<template>
  <AlienChild :msg="greeting" />
</template>