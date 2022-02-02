<script>
export default {
  data() {
    return {
      text: "",
    };
  },
};
</script>

<template>
  <div>
    <input v-model="text" placeholder="Enter text" />
    <p>{{ text }}</p>
  </div>
</template>