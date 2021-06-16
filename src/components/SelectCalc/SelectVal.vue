<template>
  <select class="selectVal" v-bind:value="calcMethod" required>
    <option v-for="item in calcMethodList" :key="item">{{ item }}</option>
  </select>
</template>

<script>
export default {
  name: "SelectVal",

  props: {
    calcMethod: {
      required: true,
    },

    calcMethodList: {
      reqired: true,
    },
  },
};
</script>

<style></style>
