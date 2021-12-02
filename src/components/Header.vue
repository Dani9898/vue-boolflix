<template>

  <header>
    <div class="logo">BOOLFLIX</div>

    <div class="search-bar">
      <input v-model="query" type="text">
      <button @click.prevent="getMovies()">Search</button>
    </div>

  </header>

</template>

<script>
import axios from "axios"


export default {
  name: 'Header',
  data() {
    return {
      query: "",
      movies: [],
      series: []

    }
  },

  methods: {
    getMovies() {
          axios
          .get(`https://api.themoviedb.org/3/search/movie?api_key=fdd22c25d6f7adc3abaeb990d06e6350&language=it-IT&query=${this.query}&include_adult=false`)
          .then((res) => {
            this.movies = res.data.results;
            this.$emit("giveMovies", this.movies);
          });

          axios
          .get(`https://api.themoviedb.org/3/search/tv?api_key=fdd22c25d6f7adc3abaeb990d06e6350&language=it-IT&query=${this.query}&include_adult=false`)
          .then((res) => {
            this.series = res.data.results;
            this.$emit("giveSeries", this.series);
          });
    

        },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

header {
  background: #222;
  height: 50px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin-bottom: 30px;

    .logo {
      color: red;
      font-size: 30px;
    }
}

</style>
