<!-- AlienComponent.vue
<script>
export default {
  emits: ['response'],
  created() {
    this.$emit('response', 'ET Phone Home!')
  }
}
</script>

<template>
  <h2>👽</h2>
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
      phoneCall: "No call yet 😱",
    };
  },
};
</script>

<template>
  <div>
    <AlienChild @response="(msg) => (phoneCall = msg)" />
    <p>{{ phoneCall }}</p>
  </div>
</template>