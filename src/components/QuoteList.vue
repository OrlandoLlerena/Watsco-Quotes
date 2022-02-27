<template>
  <div class="quoteCard">
    <v-card class="cardAlignment" elevation="8">
      <v-card-text>
        {{ savedQuote }}
      </v-card-text>
      <v-card-actions>
        <button class="deleteBtn" @click="$emit('remove', savedQuote)">
          X
        </button>
      </v-card-actions>
    </v-card>
  </div>
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
.cardAlignment {
  display: flex;
}
.quoteCard {
  margin: 20px;
}
.v-sheet.v-card {
  border-radius: 12px;
}
.deleteBtn {
  color: red;
  padding: 5px;
  font-weight: 700;
}
</style>
