<template>
  <header>
      <div class="container">
        <div class="input-wrapper">
            <input type="text" placeholder="Search title here">
            <button class="btn btn-primary">Search</button>
        </div>
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
};
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

header{
    background-color: $secondary_color;
    width: 100%;
    height: 100px;

    .container{
        height: 100%;

        .input-wrapper{
            display: flex;
            justify-content: flex-end;
            align-items: center;
            height: 100%; 

            input{
                width: 300px;
                margin-right: 10px;
                height: 30px;
                padding: 10px;
            }

            button{
                font-weight: bold;
            }
        }
    }
}

</style>