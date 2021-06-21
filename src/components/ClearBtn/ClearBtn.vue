<template>
  <button class="clearBtn" @click.prevent="clearAll">Clear</button>
</template>

<script>
export default {
  name: "ClearBtn",

  methods: {
    clearAll() {
      this.$emit("clearAll");
    },
  },
};
</script>

<style></style>
