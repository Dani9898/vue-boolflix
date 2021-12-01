<template>
  <div class="movies" v-if="moviesFiltered !== ''">
      <Movie v-for="movie, i in filteredMovies" :key="i" :details="movie" />
  </div>
</template>

<script>
import axios from "axios"
import Movie from '@/components/Movie.vue'


export default {
  name: 'Movies',
  components: {
      Movie
  },

  props: {
      moviesFiltered: String,
  },

  data() {
      return {
          movies: [],
      }
  },

  created() {
      this.getMovie()
  },

  computed: {
      filteredMovies() {
          if (this.moviesFiltered === "") {
              return this.movies
          }

          return this.movies.filter(
              (item) => item.title.toLowerCase().includes(this.moviesFiltered.toLowerCase())
          )
      }
  },

  methods: {
      getMovie() {
          axios
          .get("https://api.themoviedb.org/3/search/movie?api_key=fdd22c25d6f7adc3abaeb990d06e6350&language=it-IT&query=ritorno%20al%20futuro&include_adult=false")
          .then((res) => {
              this.movies = res.data.results;
              this.$emit("getMoviesList", this.movies);
          }) 
      },





  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.movies {
    width: 70%;
    margin: auto;
    display: flex;
    
}
</style>
