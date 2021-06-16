<template>
  <div class="calcSpace">
    <form v-on:keyup.enter.prevent="getAnswer">
      <Calc1 :calc1Value="Value1" v-model="Value1" @getInput="getInput()" />
      <SelectVal
        :calcMethod="this.chosenCalc"
        :calcMethodList="this.calcList"
      />
      <Calc2 :calc2Value="Value2" v-model="Value2" @getInput="getInput()" />
      <sumContainer :calcSum="calcSum" />

      <button class="calcSpace-btn" @click.prevent="getAnswer">
        Calculate
      </button>

      <span>Chosen: {{ this.chosenCalc }}</span>
    </form>
  </div>
</template>

<script>
import Calc1 from "../components/inputs/Calc1.vue";
import Calc2 from "../components/inputs/Calc2.vue";
import sumContainer from "../components/Sum/SumContainer.vue";
import SelectVal from "../components/SelectCalc/SelectVal.vue";

export default {
  name: "calcSpace",

  components: {
    Calc1,
    Calc2,
    sumContainer,
    SelectVal,
  },

  data() {
    return {
      Value1: 0,
      Value2: 0,
      calcSum: 0,
      chosenCalc: "",

      calcList: ["+", "-", "*", "/"],
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
