<template>
  <div class="totalsum">
    <h3 class="totalsum-sum">{{ calcSum }}</h3>
  </div>
</template>

<script>
export default {
  name: "sumContainer",

  props: {
    calcSum: {
      required: true,
    },
  },
};
</script>

<style></style>
