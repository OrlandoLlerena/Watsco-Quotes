<template>
  <header>
    <h2>My Favorite Quotes:</h2>
    <div :key="quote.id" :v-for="quote in quotes">
      <h3>{{ quote.body }}</h3>
    </div>
  </header>
</template>

<script>
export default {
  name: "QuoteList",
  props: {
    quotes: Array,
  },
};
</script>

<style scoped>
header {
  background: gray;
  color: white;
  border: 5px solid green;
  margin: 10px;
}
</style>
