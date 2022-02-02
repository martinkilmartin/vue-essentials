<!-- AlienComponent.vue
<script>
export default {
  props: {
    msg: String
  }
}
</script>

<template>
  <h2>{{ msg || 'Mommy?' }}</h2>
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
      greeting: "Mommy loves you!",
    };
  },
};
</script>

<template>
  <AlienChild :msg="greeting" />
</template>