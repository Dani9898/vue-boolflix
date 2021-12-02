<template>
  <div class="movie">

      <span v-if="movie.hasOwnProperty('title')">TITOLO: {{movie.title}}</span>
      <span v-else>TITOLO: {{movie.name}}</span>
      <span v-if="movie.hasOwnProperty('original_title')">TITOLO ORIGINALE: {{movie.original_title}}</span>
      <span v-else>TITOLO ORIGINALE: {{movie.original_name}}</span>
      <div>LINGUA: 
        <img class="flag" v-if="getLangImg(movie) !== 'non trovato' " :src="require(`../assets/img/${getLangImg(movie)}`)" :alt="movie.original_language"> 
        <span v-if="getLangImg(movie) === 'non trovato' ">
          {{movie.original_language}}
        </span>
      </div>
      
      <span>VOTO: {{movie.vote_average}}</span>

  </div>
</template>

<script>
export default {
  name: 'Movie',
  props: {
      movie: Object,
  },
  methods: {
    getLangImg(item) {
      if(item.original_language === "it") {
        return "italyflag.jpg"
      } else if (item.original_language === "en") {
        return "engflag.png"
      } else {
        return "non trovato"
      }
    }
  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.movie {
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 20%;
    background: #000;
    color: #fff;
    padding: 10px;
    border: 1px solid red;
      
      span {
        margin: 3px 0;
      }

      .flag {
        width: 20px;
      }
      
      .hidden {
        visibility: hidden;
      }

      .show {
        visibility: visible !important;
      }
}

</style>
