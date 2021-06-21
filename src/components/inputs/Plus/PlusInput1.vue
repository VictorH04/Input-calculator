<template>
  <div class="calc1">
    <label class="calc1-label">
      This plus..:
      <input
        class="calc1-input"
        type="number"
        name="calc1-input"
        id="calc1-input"
        placeholder="This plus.."
        inputmode="number"
        :value="Plus1"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Plus1",

  props: {
    Plus1: {
      required: true,
    },
  },

  methods: {
    updateValue(Plus1) {
      this.$emit("input", Plus1);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
