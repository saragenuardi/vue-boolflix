<template>
  <section>
    <h3>{{ details.original_title }}</h3>
    <h4>{{ details.title }}</h4>
    <div>
      <div v-if="details.original_language === 'it'">
        <img src="../assets/img/italia.jpg" alt="italy" />
      </div>
      <div v-else-if="details.original_language === 'ja'">
        <img src="../assets/img/giappone.jpg" alt="japan" />
      </div>
      <div v-else>
        `Bandiera non disponibile: Lang= {{ details.original_language }}`
      </div>
      {{ details.vote_average }}
    </div>
  </section>
</template>

<script>
export default {
  name: "AppFilm",
  data() {
    return {
      flagIta: "../assets/img/italia.jpg",
    };
  },
  props: {
    details: Object,
  },
  methods: {
    flagImg() {
      if (this.details.original_language === "it") {
        this.details.original_language = this.flagIta
      }
    },
  },
};
</script>

<style scoped lang="scss">
#movie {
  margin: 30px;
}
img {
  width: 20px;
}
</style> 