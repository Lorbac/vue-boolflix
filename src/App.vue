<template>
  <div id="app">
    <Header @outputSearch="inputSearch"/>
    <Main :movies="movies" :APIquery="APIquery"/>
  </div>
</template>

<script>
import axios from 'axios';
import Main from './components/Main.vue';
import Header from './components/Header.vue';

export default {
  name: 'App',
  components: {
    Main,
    Header
  },
  data() {
    return {
      APIurl:"https://api.themoviedb.org/3/search/movie?",
      APIkey:"api_key=9a2157ecf67a695b111481576d0b50c6",
      movies: [],
      APIquery:"",
    }
  },
  created() {
    this.getMovies();
  },
  methods: {
    inputSearch(text) {
      this.APIquery = text;
      this.getMovies();
    },
    getMovies() {
      axios
          .get(this.APIurl + this.APIkey + "&query=" + this.APIquery)
          .then(res => {
            this.movies = res.data.results;
          })
          .catch((error) => {
            console.log(error);
          });
    },
  }
}
</script>

<style lang="scss">
  @import './styles/general.scss';
</style>
