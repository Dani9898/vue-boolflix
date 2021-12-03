<template>
  <div class="movie">

    <div class="poster">
      <img class="found" v-if="movie.poster_path !== null " :src="`https://image.tmdb.org/t/p/original${movie.poster_path}`">
      <img class="not-found" v-else src="https://www.publicdomainpictures.net/pictures/280000/velka/not-found-image-15383864787lu.jpg" alt="image not found">
    </div>

  <div class="info">
    <span v-if="movie.hasOwnProperty('title')"><strong>Titolo:</strong> {{movie.title}}</span>
    <span v-else><strong>Titolo:</strong> {{movie.name}}</span>
    <span v-if="movie.hasOwnProperty('original_title')"><strong>Titolo originale:</strong> {{movie.original_title}}</span>
    <span v-else><strong>Titolo originale:</strong> {{movie.original_name}}</span>
    <div>Lingua originale: 
      <img class="flag" v-if="getLangImg(movie) !== 'non trovato' " :src="require(`../assets/img/${getLangImg(movie)}`)" :alt="movie.original_language"> 
      <span v-if="getLangImg(movie) === 'non trovato' ">
        {{movie.original_language}}
      </span>
    </div>
  
    <div class="vote">
      <span>Voto: </span>
        <span><i v-for="i in getVoteForFullStar(movie)" :key="i" class="fas fa-star full"></i></span>
        <span><i v-for="i in getVoteForEmptyStar()" :key="i" class="fas fa-star"></i></span>
    </div>
    


    <span v-if="movie.overview !== '' ">Overview: {{movie.overview}}</span>
    <span v-else></span>
  </div>


  </div>
</template>

<script>
export default {
  name: 'Movie',

  props: {
      movie: Object,
  },

  data() {
    return {
      fullStars: 0
    }
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
    },

    getVoteForFullStar(item) {
      this.fullStars = Math.floor(item.vote_average / 2);
      return this.fullStars
    },

    getVoteForEmptyStar() {
      let emptyStars = 5 - this.fullStars;
      return emptyStars
    }
  }
}
</script>

<style scoped lang="scss">
.movie {
    color: #fff;
    width: 20%;
    height: 400px;
    padding: 2px;
    margin: 10px 0;
    overflow: hidden;
      
      .poster {
        width: 100%;

          .found {
            max-width: 100%;
            min-height: 100%;
            object-fit: cover;
          }

          .not-found {
            width: 100%;  
          }
      }

      .info {
        display: none;
        background-color: #000;
        height: 100%;
        padding: 15px 10px;
        overflow: auto;

          span {
          font-size: 15px;
          display: block;
          margin: 4px 0;
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

        .vote {
          display: flex;

           .full {
             color:rgb(221, 189, 10)
        }
        }
        
      }
}
.movie:hover .info {
  display: block;
}
.movie:hover .poster{
  display: none;
}
</style>
