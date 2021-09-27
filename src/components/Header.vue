<template>
    <header>
        <div id="container-header">
           <a href="/" class="logoBoolfix">
               <h1> BOOLFIX </h1>
            </a> 
            <div class="col-12 inputbar" >
                <Search @performSearch="searchMovie" />
          </div>
        </div>
    </header>
</template>

<script>
import Search from './Search.vue';

export default {
  name: 'Header',
  components: {
      Search,
  },
   emits:['performSearch'],
    data() {
        return {
            inputText:'',
        }
    },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    header {
        width: 100%;
        height: 100%;

        #container-header {
            width: 100%;
            height: 100%;
            background-color: #49515f;
            display: flex;
            justify-content: space-between;
            align-items: center;
            
            .logoBoolfix {
                width: 50%;
                height: 100%;
                color: red;
            }
            
            .inputbar {
                width: 50%;
                height: 100%;
            }
        }
    }
</style>