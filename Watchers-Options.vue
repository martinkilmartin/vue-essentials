<script>
export default {
  data() {
    return {
      count: 1,
      randomUser: null,
    };
  },
  methods: {
    async fetchRandomUser() {
      this.randomUser = null;
      const res = await fetch(
        `https://jsonplaceholder.typicode.com/users/${
          Math.floor(Math.random() * 9) + 1
        }`
      );
      this.randomUser = await res.json();
    },
  },
  mounted() {
    this.fetchRandomUser();
  },
  watch: {
    count() {
      this.fetchRandomUser();
    },
  },
};
</script>

<template>
  <div>
    <p>Query Count: {{ count }}</p>
    <button @click="count++">Fetch Random User</button>
    <p v-if="!randomUser">Fetching Random User...</p>
    <pre v-else>{{ randomUser }}</pre>
  </div>
</template>