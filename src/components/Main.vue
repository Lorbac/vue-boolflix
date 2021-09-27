<template>
  <div class="container" v-if="APIquery !=''">
    <h3>Films</h3>
    <div class="films">
      <ul>
        <li v-for="(movie, index) in movies" :key="index">
          <Card :movie="movie"/>
        </li>
      </ul>
    </div>
    <h3>TV Series</h3>
    <div class="tv-series">
    <ul>
      <li v-for="(movie, index) in series" :key="index">
        <Card :movie="movie"/>
      </li>
    </ul>
    </div>
  </div>
  <h2 v-else>Inserisci una parola chiave nella ricerca</h2>
</template>

<script>
import Card from "../components/Card.vue"

export default {
  name: 'Main',
  props: {
   "movies": Array,
   "series": Array,
   "APIquery": String,
  },
  components: {
    Card,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

  .container {
    padding: 15px;

    ul {
      padding: 10px;
      list-style: none;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      
      li {
        flex-basis: 30%;
        padding: 10px;
  
      }
    }
  }

  h2 {
    text-align: center;
    margin-top: 150px;
    }

</style>
