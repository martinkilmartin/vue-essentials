<script>
export default {
  mounted() {
    this.$refs.p.textContent = '🏔'
  }
}
</script>

<template>
  <p ref="p">🧗</p>
</template>