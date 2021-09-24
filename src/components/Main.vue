<template>
    <main>
        <section id="container-main">
            <div class="box-movie">
              <div class="col-12" >
                <Search @performSearch="searchMovie" />
              </div>
                <!-- Stampo la lista dei film ottenuta tramite Axios -->
                <div v-for="(movie, index) in filteredMoviesList" :key="index" class="col-4 col-md-4 col-lg-2 mb-2">
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
          APIurl: 'https://api.themoviedb.org/3/search/movie?api_key=426a628a380ecaa161275bf9fc54a798&query=rick&language=it-IT',
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
        return item.name
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

        #container-main {
            width: 100%;
            height: 100%;
            padding: 30px;
            display: flex;
            justify-content: space-around;
            position: relative;
            //display: flex;

            .box-movie {
                width: 70%;
                height: 100%;
                background-color: white;
                position: relative;
                //display: flex;
                //justify-content: center;
                //align-items: center;
            }
        }
    }
</style>