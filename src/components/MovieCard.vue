<template>
  <div @mouseover="getApi" class="movie">
      <div class="movie-text">
        <div class="title">
            <span class="text-bold">Titolo:</span>
            {{details.title? details.title: details.name}}
        </div>
        <div class="original_title">
            <span class="text-bold">Titolo Originale:</span>
            {{details.original_title? details.original_title: details.orginale_name}}
        </div>
        <div class="language">
            <span class="text-bold">lingua:</span>
            <span v-if="availabelFlags.includes(details.original_language)">
                <img class="flag" :src="require(`../assets/${details.original_language}.png`)" :alt="details.original_language">
            </span>
            <span v-else>
                {{details.original_language}}
            </span>
               
        </div>
        <div class="vote">
            <span class="text-bold">Voto:</span>
            <span class="vote-rating">
                <i v-for="n in starRating" :key="n" id="star-rating" class="fas fa-star"></i>
                <i v-for="n in (starRatingMax - starRating)" :key="n" id="star-default" class="far fa-star"></i>
            </span>
        </div>
        <div class="cast">
            <span class="text-bold">Cast:</span>
            <span v-for="cast in castArray" :key="cast.id">
                {{cast.name}}   
            </span>
        </div>

        <div class="genre">
            <span class="text-bold">Genre:</span>
            <span v-for="genre in genreArray" :key="genre.id">
                {{genre.name}}
            </span>
        </div>
        <div class="overview">
            <span class="text-bold">Overview:</span>
            {{details.overview}}
        </div>
      </div>

      <div class="movie-img">
          <template v-if="details.poster_path != null">
            <img :src="`https://image.tmdb.org/t/p/w342/${details.poster_path}`" :alt="details.original_title? details.original_title: details.orginale_name">
          </template>
          <template v-else>
              <div class="text-bold not-find-img">
                {{details.title? details.title: details.name}}
              </div>
          </template>
        
      </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'MovieCard',
    props: {
        details: Object,
        type: String
    },
    data: function (){
        return {
            voteRating: '',
            availabelFlags: ['it', 'en', 'fr','es','de'],
            castArray: [],
            genreArray: [],
            starRatingMax: 5,
            starRating: 0
        };
    },
    methods: {
        calcVoteRating: function (){
           return this.starRating = Math.round(this.details.vote_average / 2)
        },
        getApi: function (){
            this.getCast();
            this.getGenre()
            this.calcVoteRating()
        },
        getCast: function () {
            axios.get(`https://api.themoviedb.org/3/${this.type}/${this.details.id}/credits`, {
                params: {
                    api_key: 'dc389c48e11b10c26a06091250059cac'
                }
            })
            .then((response) => {
                this.castArray = response.data.cast

                this.castArray.splice(5)

            });
        },
        getGenre: function () {
            axios.get(`https://api.themoviedb.org/3/${this.type}/${this.details.id}`, {
                params: {
                    api_key: 'dc389c48e11b10c26a06091250059cac'
                }
            })
            .then((response) => {
                this.genreArray = response.data.genres

            });
        }
    },
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';
@import '../style/general.scss';
.movie{
    color: whitesmoke;
    margin-bottom: 20px;
    min-height: 450px;
    width: 342px;

    .movie-text{
        width: 100%;
        background-color: $secondary_color;
        border: 1px solid whitesmoke;
        height: 100%;
        padding: 40px 10px;
        display: none;

        .language{

            .flag{
                width: 20px;
                margin-left: 5px;
            }
        }
         
        .vote{

            .vote-rating{
                margin-left: 5px;

                #star-rating {
                color: yellow;
                }
            }

        }
    }

    &:hover .movie-text{
        display: block;
    }

    .movie-img{
        border: 1px solid whitesmoke;
        height: 100%;
        background-image: url(../assets/bg.png);
        

        .not-find-img{
            margin: 10px;
            font-size: 20px;
            text-align: center;
        }
    }

    &:hover .movie-img{
        display: none;
    }

}

</style>