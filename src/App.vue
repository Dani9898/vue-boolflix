<template>
  <div id="app">
  
    <Header />

    <Movies />

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
  }
}
</script>

<style lang="scss">

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
