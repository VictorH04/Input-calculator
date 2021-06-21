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
        :value="Multi2"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Multi2",

  props: {
    Multi2: {
      required: true,
    },
  },

  methods: {
    updateValue(Multi2) {
      this.$emit("input", Multi2);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
