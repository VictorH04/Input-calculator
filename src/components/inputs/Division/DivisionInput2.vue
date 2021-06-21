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
        :value="Division2"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Division2",

  props: {
    Division2: {
      required: true,
    },
  },

  methods: {
    updateValue(Division2) {
      this.$emit("input", Division2);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
