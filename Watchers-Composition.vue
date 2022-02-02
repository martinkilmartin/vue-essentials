<script setup>
import { ref, watch } from "vue";

const count = ref(1);
const randomUser = ref(null);

async function fetchRandomUser() {
  randomUser.value = null;
  const res = await fetch(
    `https://jsonplaceholder.typicode.com/users/${
      Math.floor(Math.random() * 9) + 1
    }`
  );
  randomUser.value = await res.json();
}

fetchRandomUser();

watch(count, fetchRandomUser);
</script>

<template>
  <div>
    <p>Query Count: {{ count }}</p>
    <button @click="count++">Fetch Random User</button>
    <p v-if="!randomUser">Fetching Random User...</p>
    <pre v-else>{{ randomUser }}</pre>
  </div>
</template>