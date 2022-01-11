<template>
  <div class="movie">
      <div class="movie-text">
        <div class="title">
            <span class="text-bold">Titolo:</span>
            {{detailes.title}}
        </div>
        <div class="original_title">
            <span class="text-bold">Titolo Originale:</span>
            {{detailes.original_title}}
        </div>
        <div class="language">
            <span class="text-bold">lingua:</span>
            {{detailes.original_language}}
        </div>
        <div class="vote">
            <span class="text-bold">Voto:</span>
            {{detailes.vote_average}}
        </div>
      </div>

      <div class="movie-img">
          img
      </div>
  </div>
</template>

<script>
export default {
    name: 'MovieCard',
    props: {
        detailes: Object
    }
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';
@import '../style/general.scss';
.movie{
    color: whitesmoke;
    margin-bottom: 20px;

    .movie-text{
        background-color: $secondary_color;
        border: 1px solid whitesmoke;
        min-height: 400px;
        padding: 40px 10px;
        display: none;
         
    }

    &:hover .movie-text{
        display: block;
    }

    .movie-img{
        border: 1px solid whitesmoke;
        min-height: 400px;
        padding: 40px 10px;
    }

    &:hover .movie-img{
        display: none;
    }

}

</style>