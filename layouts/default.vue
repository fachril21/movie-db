<template>
  <div>
    <Header />
    <nuxt />
  </div>
</template>

<script>
import Header from "~/components/Dashboard/Header.vue";
export default {
  components: {
    Header,
  },
};
</script>
