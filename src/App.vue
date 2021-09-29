<template>
  <div id="app">
    <Header @outputSearch="inputSearch"/>
    <Main :mostPopular="mostPopular" :movies="movies" :series="series" :APIquery="APIquery"/>
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
      APIurl:"https://api.themoviedb.org/3/search/",
      APIkey:"api_key=9a2157ecf67a695b111481576d0b50c6",
      movies: [],
      series: [],
      mostPopular: [],
      APIquery:"",
    }
  },
  created() {
    this.getMostPopular();
  },
  methods: {
    inputSearch(text) {
      this.APIquery = text;
      this.getMovies();
      this.getSeries();
    },
    getMovies() {
      axios
          .get(this.APIurl + "movie?" + this.APIkey + "&query=" + this.APIquery)
          .then(res => {
            this.movies = res.data.results;
          })
          .catch((error) => {
            console.log(error);
          });
    },
    getSeries() {
      axios
          .get(this.APIurl + "tv?" + this.APIkey + "&query=" + this.APIquery)
          .then(res => {
            this.series = res.data.results;
          })
          .catch((error) => {
            console.log(error);
          });
    },
    getMostPopular() {
      axios
          .get("https://api.themoviedb.org/3/tv/popular?" + this.APIkey)
          .then(res => {
            this.mostPopular = res.data.results;
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
