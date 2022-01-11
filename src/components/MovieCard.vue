<template>
  <div class="movie">
      <div class="movie-text">
        <div class="title">
            <span class="text-bold">Titolo:</span>
        </div>
        <div class="original_title">
            <span class="text-bold">Titolo Originale:</span>
        </div>
        <div class="language">
            <span class="text-bold">lingua:</span>
        </div>
        <div class="vote">
            <span class="text-bold">Voto:</span>
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
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

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