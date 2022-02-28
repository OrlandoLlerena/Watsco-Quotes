<template lang="pug">
#app
  Header

  <v-card class="quoteContainer" elevation="12">
  <div class="box">

  h3 Quote of the Day:

  p {{ quote.body }}

  //- <!--<PwaNotification />-->

  <Button @saveQuote="addQuote" text="Save Quote" color='#679436' />

  </div>
  </v-card>

  <div v-if="savedQuotes.length">
  h2 My Favorite Quotes:
    <QuoteList v-for="(savedQuote, index) in savedQuotes" :key="index" :savedQuote="savedQuote" @remove="removeSavedQuote" />

  </div>

  <h2 v-else>Your Inspirational wisdom needs a quote.</h2>
</template>

<script>
import PwaNotification from "./components/PwaNotification.vue";
import { getRandomQuote } from "@/quotes";
import Header from "./components/Header.vue";
import QuoteList from "./components/QuoteList.vue";
import Button from "./components/Button.vue";

export default {
  name: "app",
  data() {
    return {
      quote: {
        body: null,
      },
      savedQuotes: [],
    };
  },
  components: {
    PwaNotification,
    Header,
    QuoteList,
    Button,
  },

  methods: {
    addQuote() {
      if (this.savedQuotes.includes(this.quote.body)) {
        alert("You already have this wisdom! Find another.");
      } else {
        this.savedQuotes.push(this.quote.body);
        localStorage.setItem("savedQuotes", JSON.stringify(this.savedQuotes));
      }
    },
    removeSavedQuote(selectedQuote) {
      this.savedQuotes = this.savedQuotes.filter(
        (quote) => quote !== selectedQuote
      );
      localStorage.setItem("savedQuotes", JSON.stringify(this.savedQuotes));
    },
  },
  mounted() {
    this.quote = getRandomQuote();
    this.savedQuotes = JSON.parse(localStorage.getItem("savedQuotes"));
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #2c3e50;
  min-height: 100vh;
  height: auto;
  background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
    url(./assets/shunya-koide-1emWndlDHs0-unsplash.jpg) no-repeat center center
      fixed;
  background-size: cover;
  background-position: center;
}

.box {
  margin: 8px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.btn {
  display: inline-block;
  align-self: center;
  background: black;
  color: white;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
  max-width: 200px;
}

h1 {
  color: white;
}

h2 {
  padding-left: 20px;
  color: white;
}
h3 {
  padding-left: 10px;
}

p {
  margin: 10px;
}

.quoteContainer {
  margin: 18px 8px;
}
</style>
