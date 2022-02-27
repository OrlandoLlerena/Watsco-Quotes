<template lang="pug">
  #app

    Header

    <div class="box">
    h3 Quote of the Day

    p {{ quote.body }}
    
    //- <!--<PwaNotification />-->
    <Button @saveQuote="addQuote" text="Save Quote" color='goldenrod' />
    </div>

    <div v-if="savedQuotes.length">
    <h2>My Favorite Quotes:</h2>
    
      <QuoteList v-for="(savedQuote, index) in savedQuotes" :key="index" :savedQuote="savedQuote" @remove="removeSavedQuote" />
    
    </div>

    <h3 v-else>Your Inspirational wisdom needs more wisdom.</h3>
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
body {
  background: lightgray;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.box {
  margin: 8px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.btn {
  display: inline-block;
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
</style>
