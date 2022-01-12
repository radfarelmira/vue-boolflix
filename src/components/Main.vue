<template>
  <main>
      <div class="container">
        <h1 :class="[userSearchText.length > 0? 'disactive' : 'active']">
            Boolflix
        </h1>
        
        <div :class="[userSearchText.length > 0? 'active' : 'disactive']">
            <h2>Movies</h2>
            <div class="row row-cols-2 row-cols-lg-4">
                <template v-if="moviesList.length > 0">
                    <MovieCard v-for="(movie, index) in moviesList" :key="index" :details="movie"/>
                </template>
                <template v-else>
                    Nessun risultato corrispondente alla ricerca, prova con una nuova ricerca
                </template>
            </div>
            
            <h2>Tv shows</h2>
            <div class="row row-cols-2 row-cols-lg-4">
                <template v-if="tvShowsList.length > 0">
                    <MovieCard v-for="(show, index) in tvShowsList" :key="index" :details="show"/>
                </template>
                <template v-else>
                    Nessun risultato corrispondente alla ricerca, prova con una nuova ricerca
                </template>
            </div>
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
        userSearchText: String
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

    h1{
        text-align: center;
        text-transform: uppercase;
        font-size: 100px;
        margin-top: 200px;
        color: #535353;
    }

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