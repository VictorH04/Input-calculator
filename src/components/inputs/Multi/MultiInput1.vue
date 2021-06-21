<template>
  <div class="calc1">
    <label class="calc1-label">
      This times:
      <input
        class="calc1-input"
        type="number"
        name="calc1-input"
        id="calc1-input"
        placeholder="This times:"
        inputmode="number"
        :value="Multi1"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Mutli1",

  props: {
    Multi1: {
      required: true,
    },
  },

  methods: {
    updateValue(Multi1) {
      this.$emit("input", Multi1);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
