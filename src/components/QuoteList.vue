<template>
  <li>
    {{ savedQuote }}
    <!-- <i class="fas fa-time"></i> -->
    <button @click="$emit('remove', savedQuote)">X</button>
  </li>
</template>

<script>
export default {
  name: "QuoteList",
  props: {
    savedQuote: {
      type: String,
    },
  },
};
</script>

<style scoped>
li {
  background: white;
  color: black;
  padding: 5px;
  margin: 10px;
}
</style>
