<template>
  <div id="app">

    <Header 
      @giveMovies="getMovies" 
      @giveSeries="getSeries"
    />

  <main>

    <Movies 
    :mix="mixAll"
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
      series: [],
    }
  },

  computed: {
    mixAll() {
      return [...this.movies, ...this.series]
    }
  },

  methods: {
    getMovies(items) {
      this.movies = items
    },
    getSeries(items) {
      this.series = items
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
