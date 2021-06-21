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
        :value="Plus2"
        @input="updateValue($event.target.value)"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "Plus2",

  props: {
    Plus2: {
      required: true,
    },
  },

  methods: {
    updateValue(Plus2) {
      this.$emit("input", Plus2);
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
