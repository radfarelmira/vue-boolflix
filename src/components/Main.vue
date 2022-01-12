<template>
  <main>
      <div class="container">
        <h2>Movies</h2>
            <div class="row row-cols-2 row-cols-lg-4">
                <MovieCard v-for="(movie, index) in moviesList" :key="index" :details="movie"/>
            </div>
            
        <h2>Tv shows</h2>
            <div class="row row-cols-2 row-cols-lg-4">
                <MovieCard v-for="(show, index) in tvShowsList" :key="index" :details="show"/>
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
        tvShowsList: Array,
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
    color: rgb(139, 136, 136);

    h2{
        font-weight: bold;
        color: whitesmoke;
        margin-top: 10px;
        text-transform: uppercase;

        .row{
        margin-top: 20px;
    }
    }
}

</style>