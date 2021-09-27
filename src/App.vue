<template>
  <div id="app">
    <Header @performSearch="searchMovie" />

    <Main />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
//import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  // data() {
  //   return {
  //     APIurl: 'https://api.themoviedb.org/3/search/movie?api_key=426a628a380ecaa161275bf9fc54a798&query=String&language=it-IT',
  //     apiKey: '79938ff93f3e31c05b660bffed55ce1f',
  //     moviesList: [],
  //     searchText: ''
  //   }
  // },
  // computed: {
  //   filteredMoviesList() {
  //     if (this.searchText === "") {
  //       return this.moviesList;
  //     }

  //     let filteredList = this.moviesList.filter( item => {
  //       return item.title
  //                 .toLowerCase()
  //                 .includes(this.searchText.toLowerCase());
  //     })
  //     return filteredList;
  //   }
  // },  
  // methods: {
  //   getMovies(apiParams) {
  //     axios
  //       .get(this.APIurl + 'movie', apiParams)
  //       .then(response => {
  //         console.log(response.data.sesults);
  //         this.movies = response.data.results;
  //       })
  //   },
  //   searchMovie(searchText) {
  //     const paramsObj = {
  //       params: {
  //         api_key: this.apiKey,
  //         query: searchText,
  //       }
  //     };
  //     this.getMovies(paramsObj)
  //   }
  // }
}
</script>

<style lang="scss">
  @import "./styles/general.scss";
</style>
