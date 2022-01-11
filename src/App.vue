<template>
  <div id="app">
    <Header @searchClicked="callApi"/>
    <Main :moviesList="movies"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import axios from 'axios';

export default {
  name: "App",
  components: {
    Header,
    Main , 
  },
  data: function (){
    return {
      searchedMovie:'',
      movies: [],
    };
  },
  methods: {
    callApi: function (text){
      this.searchedMovie = text;

      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'dc389c48e11b10c26a06091250059cac',
          query: this.searchedMovie
        }
      })
      .then((response) => {
        this.movies = response.data.results;
      });
    }
  },
}
</script>

<style lang="scss">
@import './style/general.scss';
@import './style/variables.scss';


</style>
