<template>
  <div class="tvseries">
    <img
      class="poster"
      :src="baseUrl + sizeImg + posterPath"
      :alt="details.original_title"
    />
    <div class="infocards">
      <h4>
        Titolo : <span>{{ details.original_name }}</span>
      </h4>
      <h4>
        Titolo Originale : <span>{{ details.name }}</span>
      </h4>

      <div v-if="details.original_language === 'it'">
        <h4>Lingua Originale:</h4>
        <img class="flags" src="../assets/img/italia.jpg" alt="italy" />
      </div>
      <div v-else-if="details.original_language === 'ja'">
        <h4>Lingua Originale:</h4>
        <img class="flags" src="../assets/img/giappone.jpg" alt="japan" />
      </div>
      <div v-else>
        <h4>Lingua Originale:</h4>
        Bandiera non disponibile: Lang= {{ details.original_language }}
      </div>

      <div class="voto">
        <h4>Voto:</h4>
        <i v-for="n in voteBase5" :key="'full' + n" class="fas fa-star full-star">
        </i>
        <i
          v-for="y in 5 - voteBase5"
          :key="'empty' + y"
          class="far fa-star empty-star"
        ></i>
      </div>

      <div class="overview">
        <h4>Overview:</h4>
        <p>{{ details.overview }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TvSeries",
  data() {
    return {
      baseUrl: "https://image.tmdb.org/t/p/",
      sizeImg: "w342/",
      posterPath: this.details.poster_path,
      originalVoteAvg: this.details.vote_average,
      voteBase5: "",
    };
  },
  props: {
    details: Object,
  },
  created() {
    this.vote1to5();
  },
  methods: {
    vote1to5() {
      console.log((this.vote = this.originalVoteAvg / 2));
      return (this.voteBase5 = Math.floor(this.originalVoteAvg / 2));
    },
  },
};
</script>

<style scoped lang="scss">

.tvseries {
    margin: 30px; 
    width: calc(100% / 4 - 60px );
    position: relative;
    
     &:hover .infocards {
          display: inline-block;
     }
   
    .infocards {
        position: absolute;
        top: 0;
        left: 0;
        color: white;
        border: 1px solid white;
        background-color: black;
        width: 100%;
        height: 100%;
        display: none;
        padding: 0 15px;
        overflow-y: auto;

        
    }
    .poster {
        border: 1px solid white;
    }
}
h4 {
    display: inline-block;
    margin-top: 10px;
}
.voto {
    margin-top: 10px;
}
.overview {
    margin-top:10px ;
    p {
        height: 40vh;
        // overflow: scroll;
    }
}


.flags{
    width: 20px;
    transform: translate(40%, 25%);
}
</style>