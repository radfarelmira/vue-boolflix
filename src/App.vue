<template>
  <div id="app">
    <Header @searchClicked="search"/>
    <Main :moviesList="moviesArray" :tvShowsList="tvShowArray" :isLoadingApi="isLoading" :userSearchText="queryValue" :isLoading="isLoadingApi"/>
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
      tvShowArray: [],
      isLoadingApi: true,
    };
  },
  methods: {
    search: function (text){
      this.queryValue = text;
      this.getMovies();
      this.getTvShows()
    },
    getMovies: function (){
      this.isLoadingApi= true;
      
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: this.apiKey,
          query: this.queryValue
        }
      })
      .then((response) => {
        this.moviesArray = response.data.results;

        this.isLoadingApi= false;
      });
    },
    getTvShows: function (){
      this.isLoadingApi= true;

      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: this.apiKey,
          query: this.queryValue
        }
      })
      .then((response) => {
        this.tvShowArray = response.data.results;

        this.isLoadingApi= false;
      });
    }
  },
}
</script>

<style lang="scss">
@import './style/general.scss';
@import './style/variables.scss';



</style>
