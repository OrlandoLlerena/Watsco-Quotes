<template>
  <header>
    <h2>My Favorite Quotes:</h2>
    <li>
      <!-- {{ todo.text }} -->
      <button @click="$emit('remove', todo.id)">X</button>
    </li>
  </header>
</template>

<script>
export default {
  name: "QuoteList",
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
