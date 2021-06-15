<template>
  <div class="calc2">
    <label class="calc2-label">
      Input 2:
      <input
        class="calc2-input"
        type="number"
        name="calc2-input"
        id="calc2-input"
        placeholder="Calc 2"
        inputmode="number"
        :value="calc2Value"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Calc2",

  props: {
    calc2Value: {
      required: true,
    },
  },

  methods: {
    updateValue(calc2Value) {
      this.$emit("input", calc2Value);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
