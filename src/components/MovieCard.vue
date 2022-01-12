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
            {{details.original_language}}
            <img :src="require(`../assets/${details.original_language}.png`)" :alt="details.original_language">   
        </div>
        <div class="vote">
            <span class="text-bold">Voto:</span>
            {{calcVoteRating()}}
            <i v-for="n in calcVoteRating()" :key="n" id="star-rating" class="fas fa-star"></i>
            <i v-for="n in (starRatingMax - calcVoteRating())" :key="n" id="star-default" class="far fa-star"></i>
            
        </div>
      </div>

      <div class="movie-img">
        <img :src="`https://image.tmdb.org/t/p/w342/${details.poster_path}`" :alt="details.original_title? details.original_title: details.orginale_name">
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
        };
    },
    methods: {
        calcVoteRating: function (){
        return  this.voteRating = Math.round(this.details.vote_average / 2)
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

    .movie-text{
        background-color: $secondary_color;
        border: 1px solid whitesmoke;
        height: 100%;
        padding: 40px 10px;
        display: none;

        .language{

            img{
                width: 20px;
            }
        }
         
        .vote{

            #star-rating{
                color: yellow;
            }
        }
    }

    &:hover .movie-text{
        display: block;
    }

    .movie-img{
        border: 1px solid whitesmoke;
        height: 100%;
    }

    &:hover .movie-img{
        display: none;
    }

}

</style>