<template>
    <main>
        <section id="container-main">
          <div class="col-12" >
            <Search @performSearch="searchMovie" />
          </div>
          <div class="box-movie row">
            <h2> Films </h2>
            <!-- Stampo la lista dei film ottenuta tramite Axios -->
            <div v-for="movie in filteredMoviesList" :key="movie.id" class="lista col-12 col-md-6 col-lg-2">
                <Movie :film="movie" /> <!-- cicla gli elementi contenuti nella componente Disc che mi sono creato -->
            </div>
          </div>
          <div class="box-serieTv row">
            <h2> Series </h2>
            <!-- Stampo la lista delle serie tv ottenuta tramite Axios -->
            <div v-for="tv in filteredSerieTvList" :key="tv.id" class="lista col-12 col-md-6 col-lg-2">
                <Movie :film="tv" /> <!-- cicla gli elementi contenuti nella componente Disc che mi sono creato -->
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
          APIurl: 'https://api.themoviedb.org/3/search/movie?api_key=426a628a380ecaa161275bf9fc54a798&query=movie&language=it-IT',
          apiKey: '79938ff93f3e31c05b660bffed55ce1f',
          pathImg: 'https://image.tmdb.org/t/p/',
          widithImg: 'http://image.tmdb.org/t/p/w500/',
           moviesList: [],
          serieTvList: [],
          searchText: ''
      }
  },
  created() {
    this.getMovie(); 
    this.getTvSeries();
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
    },
    filteredSerieTvList() {
      if (this.searchText === "") {
        return this.serieTvList;
      }

      let filteredList = this.serieTvList.filter( item => {
        return item.title
                  .toLowerCase()
                  .includes(this.searchText.toLowerCase());
      })
      return filteredList;
    }
  },  
  methods: {
    getMovie(apiParams) {
      axios
          .get(this.APIurl + 'movie' +this.pathImg + this.widithImg, apiParams) //per lanciare l'array di oggetti contenuti nell'API
          .then( res => {
            console.log(res.data.results);
            this.moviesList = res.data.results;
          })
    },
    getTvSeries(apiParams) {
      axios
          .get(this.APIurl + 'tv' +this.pathImg + this.widithImg, apiParams) //per lanciare l'array di oggetti contenuti nell'API
          .then( res => {
            console.log(res.data.results);
            this.serieTvList = res.data.results;
          })
    },
    searchMovie(text) {
      const paramsobj = {
        params: {
          api_key: this.apiKey,
          query: this.searchText,
        }
      };
      this.getMovie(paramsobj),
      this.getTvSeries(paramsobj),
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
        //height: 100%;
        background-color: #1A253A;
        position: absolute;

        #container-main {
            width: 100%;
            padding: 30px;
            // display: flex;
            // justify-content: space-around;
            // position: relative;
            
            .box-movie, .box-serieTv {
                width: 100%;
                height: 100%;
                //background-color: white;
                position: relative;
                // display: flex;
                // justify-content: space-around;
                // align-items: center;
            }

        }
    }
</style>