<template>
  <main>
      <div class="container">
        <h1 :class="[userSearchText.length > 0? 'disactive' : 'active']">
            Boolflix
        </h1>
        
        <div :class="[userSearchText.length > 0? 'active' : 'disactive']">
            <h2>Movies</h2>
            <div v-if="!isLoading" class="row row-cols-1 row-cols-lg-4">
                <template v-if="moviesList.length > 0">
                    <MovieCard v-for="movie in moviesList" :key="movie.id" :details="movie"/>
                </template>
                <template v-else>
                    Nessun risultato corrispondente alla ricerca, prova con una nuova ricerca
                </template>
            </div>
            <Loader v-else/>
            
            <h2>Tv shows</h2>
            <div v-if="!isLoading" class="row row-cols-1 row-cols-lg-4">
                <template v-if="tvShowsList.length > 0">
                    <MovieCard v-for="show in tvShowsList" :key="show.id" :details="show"/>
                </template>
                <template v-else>
                    No risults for this search, try another search
                </template>
            </div>
            <Loader v-else/>

        </div>
      </div>
  </main>
</template>

<script>
import MovieCard from "./MovieCard";
import Loader from "./Loader";


export default {
    name: 'Main',
    props:{
        moviesList: Array,
        tvShowsList: Array,
        userSearchText: String,
        isLoading: Boolean
    },
    components: {
        MovieCard,
        Loader
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