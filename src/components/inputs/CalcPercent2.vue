<template>
  <div class="calc5">
    <label class="calc5-label">
      Out of:
      <input
        class="calc5-input"
        type="number"
        name="calc5-input"
        id="calc5-input"
        placeholder="Calc 5"
        inputmode="number"
        :value="calc5Value"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Calc5",

  props: {
    calc5Value: {
      required: true,
    },
  },

  methods: {
    updateValue(calc5Value) {
      this.$emit("input", calc5Value);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
