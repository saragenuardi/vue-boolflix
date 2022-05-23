<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <AppHeader @clickBtn="userSearch" />
    <FilmLibrary />
  </div>
</template>

<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import FilmLibrary from "./components/FilmLibrary.vue";

export default {
  name: "App",
  components: {
    AppHeader,
    FilmLibrary,
  },
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/movie",
      apiKey: "b9612d6887d453afe08f46bb4d714504",
      filmList: [],
    };
  },

  methods: {
    getFilm: function (apiParams) {
      axios
        .get(this.apiUrl, apiParams)
        .then((result) => {
          this.filmsList = result.data.results;
          console.log(this.filmsList);
        })
        .catch((error) => {
          console.log("errore", error);
        });
    },

    userSearch(inputText) {
      const paramsSearch = {
        params: {
          api_key: this.apiKey,
          query: inputText,
          language: "it-IT",
        },
      };
      this.getFilm(paramsSearch);
    },
  },
};
</script>

<style lang="scss">
</style>
