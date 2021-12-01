<template>
  <div id="app">
  

    <Header 
      :moviesList="movies"
      @moviesFiltered="getMoviesFiltered"

    />

  <main>

    <Movies 
    :moviesFiltered="moviesFilter"
    @getMoviesList="getMovies" 

    />

  </main>

  </div>
</template>

<script>
import Header from './components/Header.vue'
import Movies from './components/Movies.vue'

export default {
  name: 'App',
  components: {
    Header,
    Movies
  },
  data() {
    return {
      movies: [],
      moviesFilter: ""
    }
  },
  methods: {
    getMovies(items) {
      this.movies = items
    },
    getMoviesFiltered(items) {
      this.moviesFilter = items
    }
  }
}
</script>

<style lang="scss">

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #444;
}
</style>
