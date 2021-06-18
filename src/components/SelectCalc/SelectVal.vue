<template>
  <div class="leftBtns">
    <button class="leftBtns-btn" @click.prevent="chooseCalculationPlus">
      {{ Plus }}
    </button>

    <button class="leftBtns-btn" @click.prevent="chooseCalculationMinus">
      {{ Minus }}
    </button>

    <button class="leftBtns-btn" @click.prevent="chooseCalculationDivision">
      {{ Division }}
    </button>

    <button
      class="leftBtns-btn"
      @click.prevent="chooseCalculationMultiplication"
    >
      {{ Multiplication }}
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
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
