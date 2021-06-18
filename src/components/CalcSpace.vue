<template>
  <div class="calcSpace">
    <form v-on:keyup.enter.prevent="getAnswer">
      <Calc1 :calc1Value="Value1" v-model="Value1" @getInput="getInput()" />
      <SelectVal
        @chooseCalculationPlus="chooseCalculationPlus()"
        :Plus="this.calcList.Plus"
        @chooseCalculationMinus="chooseCalculationMinus()"
        :Minus="this.calcList.Minus"
        @chooseCalculationDivision="chooseCalculationDivision()"
        :Division="this.calcList.Division"
        @chooseCalculationMultiplication="chooseCalculationMultiplication()"
        :Multiplication="this.calcList.Multiplication"
      />
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
      answer: null,

      calcList: {
        Plus: "+",
        Minus: "-",
        Division: "/",
        Multiplication: "*",
      },
    };
  },

  methods: {
    chooseCalculationPlus() {
      this.chosenCalc = Math.abs(parseInt(this.Value1) + parseInt(this.Value2));
      this.getAnswer();

      console.log(this.chosenCalc);
    },

    chooseCalculationMinus() {
      this.chosenCalc = parseInt(this.Value1) - parseInt(this.Value2);
      this.getAnswer();

      console.log(this.chosenCalc);
    },

    chooseCalculationDivision() {
      this.chosenCalc = parseInt(this.Value1) / parseInt(this.Value2);
      this.getAnswer();

      console.log(this.chosenCalc);
    },

    chooseCalculationMultiplication() {
      this.chosenCalc = parseInt(this.Value1) * parseInt(this.Value2);
      this.getAnswer();

      console.log(this.chosenCalc);
    },

    getAnswer() {
      if (this.Value1 == "") {
        alert("Please input a number!");
      } else {
        this.answer = Math.floor(this.chosenCalc * 100) / 100;

        this.calcSum = this.answer;

        console.log(this.calcSum);
        console.log(this.chosenCalc);
      }
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
