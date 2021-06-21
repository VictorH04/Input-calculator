<template>
  <div class="calc1">
    <label class="calc1-label">
      This divided by:
      <input
        class="calc1-input"
        type="number"
        name="calc1-input"
        id="calc1-input"
        placeholder="This divided by:"
        inputmode="number"
        :value="Division1"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Division1",

  props: {
    Division1: {
      required: true,
    },
  },

  methods: {
    updateValue(Division1) {
      this.$emit("input", Division1);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
