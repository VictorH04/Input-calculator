<template>
  <p class="calcSymbol">
    {{ calcSymbol }}
  </p>
</template>

<script>
export default {
  name: "CalcSymbol",

  props: {
    calcSymbol: {
      required: true,
      type: String,
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
