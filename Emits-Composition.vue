<!-- AlienComponent.vue
<script setup>
const emit = defineEmits(['response'])

emit('response', 'ET Phone Home!')
</script>

<template>
  <h2>👽</h2>
</template>
-->
<script setup>
import { ref } from "vue";
import AlienChild from "./AlienComponent.vue";

const phoneCall = ref("No call yet 😱");
</script>

<template>
  <div>
    <AlienChild @response="(msg) => (phoneCall = msg)" />
    <p>{{ phoneCall }}</p>
  </div>
</template>