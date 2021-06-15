<template>
  <div class="home">
    <h1 class="home-title">Quick Calc</h1>

    <CalcSpace />
  </div>
</template>

<script>
import CalcSpace from "../components/CalcSpace.vue";

export default {
  name: "Home",
  components: {
    CalcSpace,
  },

  data() {
    return {};
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
