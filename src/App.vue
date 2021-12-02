<template>
  <div id="app">
  <button @click="prova">asddsaasasdd</button>

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
    },
    prova(){
      console.log(this.mixAll);
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
