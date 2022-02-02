<script>
export default {
  data() {
    return {
      show: true,
    };
  },
  methods: {
    toggle() {
      this.show = !this.show;
    },
  },
};
</script>

<template>
  <div>
    <button @click="toggle">toggle</button>
    <h1 v-if="show">Sionnach Solutions is awesome! 🦊</h1>
    <h1 v-else>Sionnach Buí is even more awesome! 🦊🐈</h1>
  </div>
</template>