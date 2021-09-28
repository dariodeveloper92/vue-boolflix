<template>
  <div id="app">
    <Header @performSearch="searchMovie"/>

    <Main :moviesList="moviesList" :serieTvList="serieTvList" :searchText="inputText"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data() {
        return {
            inputText:'',
            APIurlMovie: 'https://api.themoviedb.org/3/search/movie/?api_key=426a628a380ecaa161275bf9fc54a798&query=movie&language=it-IT',
            APIurlTv: 'https://api.themoviedb.org/3/search/tv/?api_key=426a628a380ecaa161275bf9fc54a798&query=movie&language=it-IT',
            apiKey: '79938ff93f3e31c05b660bffed55ce1f',
            pathImg: 'https://image.tmdb.org/t/p/',
            widithImg: 'http://image.tmdb.org/t/p/w500/',
            moviesList: [],
            serieTvList: [],
        }
    },
    created() {
    this.search();
  },
  methods: {
    search() {
      const paramsobj = {
        params: {
          api_key: this.apiKey,
          query: this.inputText,
        }
      };
      this.getMovie(paramsobj);
      this.getTvSeries(paramsobj);
    },
    searchMovie(filter) {
      this.inputText = filter;
      this.search();
   },
    getMovie(apiParams) {
      axios
          .get(this.APIurlMovie + 'movie' +this.pathImg + this.widithImg, apiParams) //per lanciare l'array di oggetti contenuti nell'API
          .then( res => {
            console.log(res.data.results);
            this.moviesList = res.data.results;
          })
    },
    getTvSeries(apiParams) {
      axios
          .get(this.APIurlTv + 'tv' +this.pathImg + this.widithImg, apiParams) //per lanciare l'array di oggetti contenuti nell'API
          .then( res => {
            console.log(res.data.results);
            this.serieTvList = res.data.results;
          })
    },
    }
}
</script>

<style lang="scss">
  @import "./styles/general.scss";
</style>
