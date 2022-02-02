<!-- AlienComponent.vue
<template>
  <slot>The truth is out there</slot>
</template>
-->
<script>
import AlienChild from "./AlienComponent.vue";

export default {
  components: {
    AlienChild,
  },
  data() {
    return {
      msg: "👽",
    };
  },
};
</script>

<template>
  <AlienChild>{{ msg }}</AlienChild>
</template>