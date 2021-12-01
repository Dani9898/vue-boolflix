<template>
  <div class="movie">

      <span>TITOLO: {{movie.title}}</span>
      <span>TITOLO ORIGINALE: {{movie.original_title}}</span>
      <span v-if="movie.original_language === 'it' ">LINGUA ORIGINALE: <img src="../assets/img/italyflag.jpg" alt="italian"></span>
      <span v-else>LINGUA ORIGINALE: <img src="../assets/img/engflag.png" alt="italian"></span>
      <span class="hidden" :class="!languages.includes(movie.original_language) ? 'show' : '' ">LINGUA ORIGINALE: {{movie.original_language}}</span> 
      <span>VOTO: {{movie.vote_average}}</span>

  </div>
</template>

<script>
export default {
  name: 'Movie',
  props: {
      movie: Object,
  },
  data(){
    return {
      languages: ["it", "en"]
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

          img {
            width: 20px;
          };
      }
      
      .hidden {
        visibility: hidden;
      }

      .show {
        visibility: visible !important;
      }
}

</style>
