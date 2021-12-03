<template>
  <div id="app">

    <Header 
      @giveMovies="getMovies" 
      @giveSeries="getSeries"
      @giveQuery="getQuery"
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
      query: ""
    }
  },

  computed: {
    mixAll() {
      if(this.query.trim() !== "") {
        return [...this.movies, ...this.series]
      } else {
        return []
      }
      
    }
  },

  methods: {
    getMovies(items) {
      this.movies = items
    },
    getSeries(items) {
      this.series = items
    },
    getQuery(item) {
      this.query = item
    }
  }
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.min.css';

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #444;
}
</style>
