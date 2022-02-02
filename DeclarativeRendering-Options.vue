<script>
export default {
  data() {
    return {
      message: 'Hi Earthlings!'
    }
  }
}
</script>

<template>
  <h1>{{ message.split('').reverse().join('') }}</h1>
</template>