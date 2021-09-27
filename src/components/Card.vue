<template>
<div class="card">
    <div class="card-movie" v-if="movie.title">
        <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" :alt="`${movie.title}`">
        <h3>{{ movie.title }}</h3>
        <p>Titolo originale: {{ movie.original_title }}</p>
        <div>Voto: <i v-for="i in getVote()" :key="i" class="fas fa-star"></i></div>
        <img class="flags" :src="require(`../assets/${movie.original_language}.png`)" :alt="`${movie.original_language}`">
    </div>

    <div class="card-series" v-else>
        <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" :alt="`${movie.name}`">
        <h3>{{ movie.name }}</h3>
        <p>Titolo originale: {{ movie.original_name }}</p>
        <p>Voto: <i v-for="i in getVote()" :key="i" class="fas fa-star"></i></p>
        <img class="flags" :src="require(`../assets/${movie.original_language}.png`)" :alt="`${movie.original_language}`">
    </div>
</div>


</template>

<script>
export default {
  name: 'Card',
  props: {
    "movie": Object,
  },
  methods: {
    getVote() {
        return Math.ceil(this.movie.vote_average / 2);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    @import '~@fortawesome/fontawesome-free/css/all.min.css';

    .card {

        .poster, h3, p, div {
            width: 100%;
            color: white;
        }

        .poster {
            height: 440px;
        }

        h3 {
            font-size: 12px;
        }
        
        p {
            font-size: 10px;
        }

        .flags {
            width: 5%;
        }

        i {
            color: yellow;
        }
    }
</style>