<template>
    <main>
        <section id="container-main">
            <div class="box-movie">
              <div  class="col-12">
                <Search @performSearch="searchGenre" />
              </div>
                <!-- Stampo la lista dei film ottenuta tramite Axios -->
            </div>
            
        </section>
    </main>
</template>

<script>
//import axios from 'axios';
import Search from './Search.vue';

export default {
  name: 'Main',
  components: {
      Search
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    main {
        width: 100%;
        height: 90vh;
        background-color: #1A253A;

        #container-main {
            width: 100%;
            height: 100%;
            padding: 30px;
            display: flex;
            justify-content: center;
            position: relative;

            .box-movie {
                width: 70%;
                height: 100%;
                background-color: white;
                position: relative;
                display: flex;
                justify-content: center;
            }
        }
    }
</style>