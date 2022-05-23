<template>
  <section>
    <h3>{{ details.original_title }}</h3>
    <h4>{{ details.title }}</h4>
    <div>{{ details.original_language }}</div>
    <div>{{ details.vote_average }}</div>
  </section>
</template>

<script>
export default {
  name: "AppFilm",
  props: {
    details: Object,
  },
};
</script>

<style scoped lang="scss">
#movie {
  margin: 30px;
}
</style> 