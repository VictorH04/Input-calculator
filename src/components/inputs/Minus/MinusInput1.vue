<template>
  <div class="calc1">
    <label class="calc1-label">
      This minus:
      <input
        class="calc1-input"
        type="number"
        name="calc1-input"
        id="calc1-input"
        placeholder="This minus:"
        inputmode="number"
        :value="Minus1"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Minus1",

  props: {
    Minus1: {
      required: true,
    },
  },

  methods: {
    updateValue(Minus1) {
      this.$emit("input", Minus1);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
