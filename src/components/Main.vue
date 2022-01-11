<template>
  <main>
      <div class="container">
          <div class="row row-cols-2 row-cols-lg-4">
              <div class="card">
                  
              </div>
          </div>
      </div>
  </main>
</template>

<script>
export default {
    name: 'Main',

}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

main{
    width: 100%;
    height: calc(100vh - 100px);
    background-color: $primary_color;
}

</style>