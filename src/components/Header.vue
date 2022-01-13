<template>
  <header>
      <div class="container">  
        <div class="header-wrapper">
            <h2>Boolflix</h2>
            <div class="header-search">
                <input v-model="userSearchText" type="text" placeholder="Search title here">
                <button @click="$emit('searchClicked', userSearchText)" class="btn btn-primary">Search</button>
            </div>   
        </div>
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data: function (){
        return {
            userSearchText: ''
        };    
    },
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

        .header-wrapper{
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            height: 100%;
            
            h2{
                color: red;
                font-size: 40px;
                text-transform: uppercase;
            }

            input{
                max-width: 300px;
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