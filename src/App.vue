<template>
  <div id="app">
    <Header @searchClicked="search"/>
    <Main :moviesList="moviesArray" :tvShowsList="tvShowArray"/>
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
      queryValue:'',
      apiKey: 'dc389c48e11b10c26a06091250059cac',
      moviesArray: [],
      tvShowArray: []
    };
  },
  methods: {
    search: function (text){
      this.queryValue = text;
      this.getMovies();
      this.getTvShows()
    },
    getMovies: function (){
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: this.apiKey,
          query: this.queryValue
        }
      })
      .then((response) => {
        this.moviesArray = response.data.results;
      });
    },
    getTvShows: function (){
      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: this.apiKey,
          query: this.queryValue
        }
      })
      .then((response) => {
        this.tvShowArray = response.data.results;
        console.log(this.tvShowArray)
      });
    }
  },
}
</script>

<style lang="scss">
@import './style/general.scss';
@import './style/variables.scss';



</style>
