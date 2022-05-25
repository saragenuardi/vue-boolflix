<template>
  <section>
    <AppFilm 
     v-for ="movie in moviesList"
     :key="movie.id"
     :details="movie"
    />
    <TvSeries
     v-for ="tv in tvList"
     :key="tv.id"
     :details="tv"
    />
  </section>
</template>

<script>

import AppFilm from "../components/AppFilm.vue";
import TvSeries from '../components/TvSeries.vue'

export default {
  name: "FilmLibrary",
  components: {
    AppFilm,
    TvSeries
  },
  data() {
    return {};
  },
  props: {
      moviesList: Array,
      tvList: Array
  },
  created() {},
  comupted: {},
  methods: {},
};
</script>

<style scoped lang="scss">
section {
    display: flex;
    flex-wrap: wrap;
    margin: 0 auto;
}
</style> 