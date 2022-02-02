<script>
export default {
  data() {
    return {
      count: 0
    }
  },
  methods: {
    inc() {
      this.count++
    }
  }
}
</script>

<template>
  <button @click="inc">{{ count }}</button>
</template>