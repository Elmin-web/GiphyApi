<template>
  <div id="app">
    <Search @search:gif="searchGif" />
    <Prewiew :isLoading="isLoading" :gifs="gifs" />
  </div>
</template>
<script>
import Search from "./components/Search.vue";
import Prewiew from "./components/Prewiew.vue";

export default {
  name: "App",
  data() {
    return {
      gifs: [],
      isLoading: false,
    };
  },
  components: {
    Search,
    Prewiew,
  },
  methods: {
    searchGif(query) {
      this.isLoading = true;
      this.gifs = [];
      fetch(
        `https://api.giphy.com/v1/gifs/search?api_key=5GMRCISEfzvkP4GETWsYy87Ww4jFNITM&q=${query}`
      )
        .then((res) => res.json())
        .then((res) => {
          this.gifs = res.data;
          this.isLoading = false;
        });
    },

  },
  created() {
    this.isLoading = true;
    fetch(
      "https://api.giphy.com/v1/gifs/trending?apiKey=5GMRCISEfzvkP4GETWsYy87Ww4jFNITM&api_key=dc6zaTOxFJmzC"
    )
      .then((res) => res.json())
      .then((res) => {
        this.gifs = res.data;
        this.isLoading = false;
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
