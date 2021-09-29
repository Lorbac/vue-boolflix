<template>
  <div class="wrapper">
    <div class="container" v-if="APIquery !=''">
      <h3>Film</h3>
      <div id="films" class="films">
        <div id="right" @click="rightScrollFilm()" class="slide-right"><i class="fas fa-chevron-right"></i></div>
        <div id="left" @click="leftScrollFilm()" class="slide-left"><i class="fas fa-chevron-left"></i></div>
        <ul>
          <li v-for="movie in movies" :key="movie.id">
            <Card :movie="movie"/>
          </li>
        </ul>
      </div>
      <h3>Serie TV</h3>
      <div id="tv-series" class="tv-series">
        <div id="right" @click="rightScrollSerie()" class="slide-right"><i class="fas fa-chevron-right"></i></div>
        <div id="left" @click="leftScrollSerie()" class="slide-left"><i class="fas fa-chevron-left"></i></div>
      <ul>
        <li v-for="movie in series" :key="movie.id">
          <Card :movie="movie"/>
        </li>
      </ul>
      </div>
    </div>
    <h2 v-else>Inserisci una parola chiave nella ricerca</h2>
  </div>
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
  methods: {
    rightScrollFilm() {
      return document.getElementById("films").scrollLeft += 800;
    },
    leftScrollFilm() {
      return document.getElementById("films").scrollLeft -= 800;
    },
    rightScrollSerie() {
      return document.getElementById("tv-series").scrollLeft += 800;
    },
    leftScrollSerie() {
      return document.getElementById("tv-series").scrollLeft -= 800;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

  .container {
    height: calc(100vh - 80px);
    width: 100%;
    background-color: #222222;
    overflow-y: auto;
    position: relative;
    
    .films {
      overflow-x: hidden;
      scroll-behavior: smooth;

      .slide-right {
        position: absolute;
        z-index: 9999;
        font-size: 50px;
        color: white;
        top: 215px;
        right: 10px;
        cursor: pointer;
        background-color: rgba(0,0,0,0.5);
        padding: 20px 10px;
        border-radius: 100px;
      }

      .slide-left {
        position: absolute;
        z-index: 9999;
        font-size: 50px;
        color: white;
        top: 215px;
        left: 10px;
        cursor: pointer;
        background-color: rgba(0,0,0,0.5);
        padding: 20px 10px;
        border-radius: 100px;
      }
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
      overflow-x: hidden;
      scroll-behavior: smooth;

      .slide-right {
        position: absolute;
        z-index: 9999;
        font-size: 50px;
        color: white;
        bottom: 60px;
        right: 10px;
        cursor: pointer;
        background-color: rgba(0,0,0,0.5);
        padding: 20px 10px;
        border-radius: 100px;
      }

      .slide-left {
        position: absolute;
        z-index: 9999;
        font-size: 50px;
        color: white;
        bottom: 60px;
        left: 10px;
        cursor: pointer;
        background-color: rgba(0,0,0,0.5);
        padding: 20px 10px;
        border-radius: 100px;
      }
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
      padding: 5px 15px 0 15px;
      font-size: 22px;
    }

    ul {
      list-style: none;
      display: flex;
      
      li {
        width: 100%;
        padding: 5px 0;
      }
    }
  }

  h2 {
    text-align: center;
    margin-top: 150px;
    }

</style>
