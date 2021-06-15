<template>
  <div class="calcSpace">
    <form @submit.prevent="getAnswer">
      <Calc1 :calc1Value="Value1" v-model="Value1" @getInput="getInput()" />
      <Calc2 :calc2Value="Value2" v-model="Value2" @getInput="getInput()" />
      <sumContainer :calcSum="calcSum" />

      <button class="calcSpace-btn" @click.prevent="getAnswer">
        Calculate
      </button>
    </form>
  </div>
</template>

<script>
import Calc1 from "../components/inputs/Calc1.vue";
import Calc2 from "../components/inputs/Calc2.vue";
import sumContainer from "../components/Sum/SumContainer.vue";

export default {
  name: "calcSpace",

  components: {
    Calc1,
    Calc2,
    sumContainer,
  },

  data() {
    return {
      Value1: 0,
      Value2: 0,
      calcSum: 0,
    };
  },

  methods: {
    getAnswer() {
      let answer = parseInt(this.Value1) + parseInt(this.Value2);

      this.calcSum = answer;

      console.log(this.calcSum);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
