<template>
  <div class="calc4">
    <label class="calc4-label">
      %:
      <input
        class="calc4-input"
        type="number"
        name="calc4-input"
        id="calc4-input"
        placeholder="Value %"
        inputmode="number"
        :value="calc4Value"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Calc4",

  props: {
    calc4Value: {
      required: true,
    },
  },

  methods: {
    updateValue(calc4Value) {
      this.$emit("input", calc4Value);
    },

    updateValue2(calc5Value) {
      this.$emit("input", calc5Value);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
