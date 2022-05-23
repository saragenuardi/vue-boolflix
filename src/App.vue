<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <AppHeader @clickBtn="userSearch" />
    <FilmLibrary :moviesList="filmsList" :tvList="tvSeries" />
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
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "b9612d6887d453afe08f46bb4d714504",
      filmList: [],
      tvSeries: []
    };
  },

  methods: {
    getFilm: function (apiParams) {
      axios
        .get(this.apiUrl + 'movie', apiParams)
        .then((result) => {
          this.filmsList = result.data.results;
          console.log("film",this.filmsList);
        })

        .catch((error) => {
          console.log("errore", error);
        })

    },
     getTvSeries: function(apiParams) {
      axios
      .get(this.apiUrl +'tv',apiParams)
      .then((result) => {
        this.tvSeries = result.data.results;
        console.log("serie",this.tvSeries);
      })
      
    userSearch(inputText), {
      const: paramsSearch = {
        params: {
          api_key: this.apiKey,
          query: inputText,
          language: "it-IT",
        },
      };
      this.getFilm(paramsSearch);
      this.getTvSeries(paramsSearch)
    },
  },
};
</script>

<style lang="scss">
</style>
