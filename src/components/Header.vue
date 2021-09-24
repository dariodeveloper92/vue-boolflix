<template>
    <header>
        <div id="container-header">
           <div class="logoBoolfix">
               <h1> BOOLFIX </h1>
            </div> 
            <!-- <div  id="select">
                <Search @performSearch="searchGenre" />
            </div> -->
        </div>
    </header>
</template>

<script>
//import Search from './Search.vue'

export default {
  name: 'Header',
  components: {
      //Search,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    header {
        width: 100%;
        height: 10vh;

        #container-header {
            width: 100%;
            height: 100%;
            background-color: #49515f;
            
            .logoBoolfix {
                width: 100%;
                height: 100%;
                color: red;
                display: flex;
                justify-content: flex-start;
                align-items: center;
                              
            }
            // #select {
            //     width: 100%;
            //     height: 100%;
            //     background-color: white;
            //     display: flex;
            //     justify-content: flex-end;
            //     align-items: center;
            // }
        }
    }
</style>