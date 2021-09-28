<template>
  <div class="container" v-if="APIquery !=''">
    <h3>Film</h3>
    <div class="films">
      <ul>
        <li v-for="movie in movies" :key="movie.id">
          <Card :movie="movie"/>
        </li>
      </ul>
    </div>
    <h3>Serie TV</h3>
    <div class="tv-series">
    <ul>
      <li v-for="movie in series" :key="movie.id">
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
    height: calc(100vh - 80px);
    width: 100%;
    background-color: #222222;
    
    .films {
      overflow-x: auto;
    }

    .films::-webkit-scrollbar {
      width: 5px;
      height: 8px;
      background-color: #aaa;
    }

    .films::-webkit-scrollbar-thumb {
      background: #000;
    }

    .tv-series {
      overflow-x: auto;
    }

    .tv-series::-webkit-scrollbar-thumb {
      background: #000;
    }

    .tv-series::-webkit-scrollbar {
      width: 5px;
      height: 8px;
      background-color: #aaa;
    }

    h3 {
      color: white;
      padding: 0 15px;
      font-size: 25px;
      border-bottom: 1px solid red;
    }

    ul {
      padding: 10px 0;
      list-style: none;
      display: flex;
      
      li {
        flex-basis: calc((100% / 6) - 10px);
        padding: 5px 0;
      }
    }
  }

  h2 {
    text-align: center;
    margin-top: 150px;
    }

</style>
