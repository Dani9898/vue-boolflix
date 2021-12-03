<template>
  <div class="movies">

    <Movie v-for="item, i in mix" 
    :key="i" 
    :movie="item" 
    />
    
  </div>
</template>

<script>
import Movie from '@/components/Movie.vue'


export default {
  name: 'Movies',

  components: {
      Movie
  },
  props: {
      mix: Array
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.movies {
    width: 70%;
    margin: auto;
    display: flex;
    flex-wrap: wrap;
    
}
</style>
