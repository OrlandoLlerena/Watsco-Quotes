<template lang="pug">
  #app
    Header
    <div class="box">
    h3 Quote of the Day
    a(
      v-if="quote.link"
      :href="quote.link"
    ) {{ quote.body }}

    span(v-else) {{ quote.body }}
    
    <!--<PwaNotification />-->
    <Button text="Save Quote" color='goldenrod' />
    </div>
    QuoteList
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
      quote: null,
    };
  },
  components: {
    PwaNotification,
    Header,
    QuoteList,
    Button,
  },
  mounted() {
    this.quote = getRandomQuote();
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  border: 3px solid red;
}

.box {
  border: 3px solid blue;
  margin: 8px;
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
}
</style>
