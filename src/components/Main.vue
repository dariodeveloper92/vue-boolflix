<template>
    <main>
        <section id="container-main">
          <div class="box-movie row">
            <h2> Films </h2>
            <!-- Stampo la lista dei film ottenuta tramite Axios -->
            <div v-for="movie in moviesList" :key="movie.id" class="lista col-12 col-md-6 col-lg-2">
                <Movie :film="movie" /> <!-- cicla gli elementi contenuti nella componente Disc che mi sono creato -->
            </div>
          </div>
          <div class="box-serieTv row">
            <h2> Series </h2>
            <!-- Stampo la lista delle serie tv ottenuta tramite Axios -->
            <div v-for="tv in serieTvList" :key="tv.id" class="lista col-12 col-md-6 col-lg-2">
                <Movie :film="tv" /> <!-- cicla gli elementi contenuti nella componente Disc che mi sono creato -->
            </div>
          </div>
        </section>
    </main>
</template>

<script>
import Movie from './Movie.vue';

export default {
  name: 'Main',
  components: {
    Movie
  },
  props: ['moviesList', 'serieTvList'],
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    main {
      width: 100%;
      min-height: 100vh;
      background-color: #1A253A;
      position: relative;

      #container-main {
        width: 100%;
        //height: 100vh;
        //padding: 30px;
        color: white;
        position: relative;
            
        .box-movie, .box-serieTv {
          width: 100%;
          height: 100%;
          position: relative;
        }
      }
    }
</style>