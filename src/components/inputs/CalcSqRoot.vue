<template>
  <div class="calc3">
    <label class="calc3-label">
      Square root of:
      <input
        class="calc3-input"
        type="number"
        name="calc3-input"
        id="calc3-input"
        placeholder="Calc 3"
        inputmode="number"
        :value="calc3Value"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Calc3",

  props: {
    calc3Value: {
      required: true,
    },
  },

  methods: {
    updateValue(calc3Value) {
      this.$emit("input", calc3Value);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
