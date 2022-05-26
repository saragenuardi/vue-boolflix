<template>
  <div id="app">
    <AppHeader @clickBtn="userSearch" />
    <FilmLibrary :moviesList="filmList" :tvList="tvSeries" />
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
      tvSeries: [],
    };
  },

  methods: {
    getFilm: function (apiParams) {
      axios
        .get(this.apiUrl + "movie", apiParams)
        .then((result) => {
          this.filmsList = result.data.results;
          console.log("film", this.filmsList);
        })
        .catch((error) => {
          console.log("errore", error);
        });
    },
    getTvSeries: function (apiParams) {
      axios.get(this.apiUrl + "tv", apiParams).then((result) => {
        this.tvSeries = result.data.results;
        console.log("serie", this.tvSeries);
      });
    },

    userSearch: function (inputText) {
      const paramsSearch = {
        params: {
          api_key: this.apiKey,
          query: inputText,
          language: "it-IT",
        },
      };

      this.getFilm(paramsSearch);
      this.getTvSeries(paramsSearch);
    },
  },
};
</script>

<style lang="scss">
@import "~@fortawesome/fontawesome-free/css/all.min.css";
body {
  background-color: #434343;
}
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  color: white;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
