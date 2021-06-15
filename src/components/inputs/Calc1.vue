<template>
  <div class="calc1">
    <label class="calc1-label">
      Input 1:
      <input
        class="calc1-input"
        type="number"
        name="calc1-input"
        id="calc1-input"
        placeholder="Calc 1"
        inputmode="number"
        :value="calc1Value"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Calc1",

  props: {
    calc1Value: {
      required: true,
    },
  },

  methods: {
    updateValue(calc1Value) {
      this.$emit("input", calc1Value);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
