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
    
    </div>
    QuoteList
</template>

<script>
import PwaNotification from "./components/PwaNotification.vue";
import { getRandomQuote } from "@/quotes";
import Header from "./components/Header.vue";
import QuoteList from "./components/QuoteList.vue";

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
</style>
