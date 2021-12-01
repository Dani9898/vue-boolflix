<template>
  <div class="movie">

      <span>{{details.title}}</span>
      <span>{{details.original_title}}</span>
      <span>{{details.original_language}}</span>
      <span>{{details.vote_average}}</span>

  </div>
</template>

<script>
export default {
  name: 'Movie',
  props: {
      details: Object
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.movie {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 20%;
    background: #000;
    color: #fff;
    padding: 10px;
    border: 1px solid red;
}
</style>
