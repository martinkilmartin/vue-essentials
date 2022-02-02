<!-- AlienComponent.vue
<template>
  <h2>Congratulations! It's an alien! 👽</h2>
</template>
-->
<script>
import AlienChild from "./AlienComponent.vue";

export default {
  components: {
    AlienChild,
  },
};
</script>

<template>
  <AlienChild />
</template>