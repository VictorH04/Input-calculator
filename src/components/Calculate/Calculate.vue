<template>
  <button class="CalcBtn" @click.prevent="Calculate">Calculate</button>
</template>

<script>
export default {
  name: "CalcBtn",

  methods: {
    Calculate() {
      this.$emit("Calculate");
    },
  },
};
</script>

<style></style>
