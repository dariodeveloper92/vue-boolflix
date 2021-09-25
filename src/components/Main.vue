<template>
    <main>
        <section id="container-main">
          <div class="col-12" >
                <Search @performSearch="searchMovie" />
              </div>
            <div class="box-movie">
              <!-- Stampo la lista dei film ottenuta tramite Axios -->
              <div v-for="(movie, index) in filteredMoviesList" :key="index" class="lista">
                  <Movie :film="movie" /> <!-- cicla gli elementi contenuti nella componente Disc che mi sono creato -->
              </div>
            </div>
            
        </section>
    </main>
</template>

<script>
import axios from 'axios';
import Search from './Search.vue';
import Movie from './Movie.vue';

export default {
  name: 'Main',
  components: {
      Search,
      Movie
  },
  data() {
      return {
          APIurl: 'https://api.themoviedb.org/3/search/movie?api_key=426a628a380ecaa161275bf9fc54a798&query=String&language=it-IT',
          moviesList: [],
          searchText: ''
      }
  },
  created() {
    this.getMovie(); 
  },
  computed: {
    filteredMoviesList() {
      if (this.searchText === "") {
        return this.moviesList;
      }

      let filteredList = this.moviesList.filter( item => {
        return item.title
                  .toLowerCase()
                  .includes(this.searchText.toLowerCase());
      })
      return filteredList;
    }
  },  
  methods: {
    getMovie() {
      axios
          .get(this.APIurl) //per lanciare l'array di oggetti contenuti nell'API
          .then( res => {
            console.log(res.data.results);
            this.moviesList = res.data.results;
          })
    },
    searchMovie(text) {
      console.log(text);
      this.searchText = text;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    main {
        width: 100%;
        height: 90vh;
        background-color: #1A253A;
        position: absolute;

        #container-main {
            width: 100%;
            height: 100%;
            // padding: 30px;
            // display: flex;
            // justify-content: space-around;
            // position: relative;
            
            .box-movie {
                width: 100%;
                height: 100%;
                background-color: white;
                position: relative;
                display: flex;
                justify-content: space-around;
                align-items: center;
            
              .lista {
                display: flex;
              }
            }

        }
    }
</style>