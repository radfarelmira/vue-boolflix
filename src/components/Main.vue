<template>
  <main>
      <div class="container">
          <div class="row row-cols-2 row-cols-lg-4">
            <MovieCard />
          </div>
      </div>
  </main>
</template>

<script>
import MovieCard from "./MovieCard";

export default {
    name: 'Main',
    components: {
        MovieCard,
    },
};
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

main{
    width: 100%;
    height: calc(100vh - 100px);
    background-color: $primary_color;
    overflow-y: auto;

    .row{
        margin-top: 20px;
    }
}

</style>