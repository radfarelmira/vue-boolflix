<template>
  <main>
      <div class="container">
          <h2>MOVIES</h2>
          <div class="row row-cols-2 row-cols-lg-4">
            <MovieCard v-for="(movie, index) in moviesList" :key="index" :detailes="movie"/>
          </div>

          <div class="row row-cols-2 row-cols-lg-4">
            <h2>TV SHOWS</h2>
            <MovieCard v-for="(show, index) in tvShowsList" :key="index"/>
          </div>
          
      </div>
  </main>
</template>

<script>
import MovieCard from "./MovieCard";

export default {
    name: 'Main',
    props:{
        moviesList: Array,
        tvShowsList: Array
    },
    components: {
        MovieCard,
    }
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

main{
    width: 100%;
    height: calc(100vh - 100px);
    background-color: $primary_color;
    overflow-y: auto;

    .row{
        margin-top: 20px;
    }
}

</style>