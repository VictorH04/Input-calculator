<template>
  <div class="leftBtns">
    <button
      title="Plus"
      class="leftBtns-btn"
      @click.prevent="chooseCalculationPlus"
    >
      {{ Plus }}
    </button>

    <button
      title="Minus"
      class="leftBtns-btn"
      @click.prevent="chooseCalculationMinus"
    >
      {{ Minus }}
    </button>

    <button
      title="Division"
      class="leftBtns-btn"
      @click.prevent="chooseCalculationDivision"
    >
      {{ Division }}
    </button>

    <button
      title="Multiplication"
      class="leftBtns-btn"
      @click.prevent="chooseCalculationMultiplication"
    >
      {{ Multiplication }}
    </button>

    <button
      title="Square Root"
      class="leftBtns-btn"
      @click.prevent="chooseCalculationSquareRoot"
    >
      {{ SquareRoot }}
    </button>

    <button
      title="Percent"
      class="leftBtns-btn"
      @click.prevent="chooseCalculationPercent"
    >
      {{ Percent }}
    </button>
  </div>
</template>

<script>
export default {
  name: "SelectVal",

  props: {
    Plus: {
      required: true,
      type: String,
    },

    Minus: {
      required: true,
      type: String,
    },

    Division: {
      required: true,
      type: String,
    },

    Multiplication: {
      required: true,
      type: String,
    },

    SquareRoot: {
      required: true,
      type: String,
    },

    Percent: {
      required: true,
      type: String,
    },
  },

  methods: {
    chooseCalculationPlus() {
      this.$emit("chooseCalculationPlus");
    },

    chooseCalculationMinus() {
      this.$emit("chooseCalculationMinus");
    },

    chooseCalculationDivision() {
      this.$emit("chooseCalculationDivision");
    },

    chooseCalculationMultiplication() {
      this.$emit("chooseCalculationMultiplication");
    },

    chooseCalculationSquareRoot() {
      this.$emit("chooseCalculationSquareRoot");
    },

    chooseCalculationPercent() {
      this.$emit("chooseCalculationPercent");
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
