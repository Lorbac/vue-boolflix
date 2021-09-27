<template>
  <div class="container" v-if="APIquery !=''">
    <h3>Film</h3>
    <div class="films">
      <ul>
        <li v-for="(movie, index) in movies" :key="index">
          <Card :movie="movie"/>
        </li>
      </ul>
    </div>
    <h3>Serie TV</h3>
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
    background-color: #222222;

    h3 {
      color: white;
      padding: 15px;
      font-size: 30px;
      border-bottom: 1px solid red;
    }

    ul {
      padding: 10px 0;
      list-style: none;
      display: flex;
      flex-wrap: wrap;
      
      li {
        flex-basis: calc((100% / 6));
      }
    }
  }

  h2 {
    text-align: center;
    margin-top: 150px;
    }

</style>
