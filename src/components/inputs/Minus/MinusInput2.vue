<template>
  <div class="calc2">
    <label class="calc2-label">
      that!:
      <input
        class="calc2-input"
        type="number"
        name="calc2-input"
        id="calc2-input"
        placeholder="that!"
        inputmode="number"
        :value="Minus2"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Minus2",

  props: {
    Minus2: {
      required: true,
    },
  },

  methods: {
    updateValue(Minus2) {
      this.$emit("input", Minus2);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
