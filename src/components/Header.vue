<template>

  <header>
    <div class="logo">BOOLFLIX</div>

    <div class="search-bar">
      <input v-model="movieFilter" type="text">
      <button @click="$emit('giveMoviesFiltered', movieFilter)">Search</button>
    </div>

  </header>

</template>

<script>
export default {
  name: 'Header',
  props: {
    moviesList: Array
  },
  data() {
    return {
      movieFilter: "",

    }
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
