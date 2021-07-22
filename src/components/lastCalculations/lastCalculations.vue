<template>
  <div class="lastCalculations">
    <h1 class="lastCalculations-title">Last calculations</h1>
    <transition-group name="slide-fade" tag="p">
      <p class="lastCalculations-text" v-for="item in answerArrays" :key="item">
        {{ item }}
      </p>
    </transition-group>
  </div>
</template>

<script>
export default {
  name: "lastCalculations",

  props: {
    answerArrays: {
      required: true,
      //   type: Array,
    },
  },

  data() {
    return {};
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
