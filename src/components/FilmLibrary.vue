<template>
  <section>
    <AppFilm 
    v-for ="movie, i in moviesList"
     :key="i"
     :details="movie"
    />
  </section>
</template>

<script>

import AppFilm from "../components/AppFilm.vue";
export default {
  name: "FilmLibrary",
  components: {
    AppFilm,
  },
  data() {
    return {};
  },
  props: {
      moviesList: Array
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