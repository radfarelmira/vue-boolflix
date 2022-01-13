<template>
  <div class="movie">
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
                <i v-for="n in calcVoteRating()" :key="n" id="star-rating" class="fas fa-star"></i>
                <i v-for="n in (starRatingMax - calcVoteRating())" :key="n" id="star-default" class="far fa-star"></i>
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
export default {
    name: 'MovieCard',
    props: {
        details: Object,
    },
    data: function (){
        return {
            voteRating: '',
            starRatingMax: 5,
            availabelFlags: ['it', 'en', 'fr','es','de']
        };
    },
    methods: {
        calcVoteRating: function (){
        return Math.round(this.details.vote_average / 2)
        }
    }
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';
@import '../style/general.scss';
.movie{
    color: whitesmoke;
    margin-bottom: 20px;
    min-height: 400px;
    min-width: 200px;

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