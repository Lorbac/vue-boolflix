<template>
<div class="card">
    <div class="card-movie" v-if="movie.title">
        <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt="">
        <h3>{{ movie.title }}</h3>
        <p>Titolo originale: {{ movie.original_title }}</p>
        <p>Media voti: {{ movie.vote_average }}</p>
        <img class="flags" :src="require(`../assets/${movie.original_language}.png`)" alt="">
    </div>

    <div class="card-series" v-else>
        <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt="">
        <h3>{{ movie.name }}</h3>
        <p>Titolo originale: {{ movie.original_name }}</p>
        <p>Media voti: {{ movie.vote_average }}</p>
        <img class="flags" :src="require(`../assets/${movie.original_language}.png`)" alt="">
    </div>
</div>


</template>

<script>
export default {
  name: 'Card',
  props: {
    "movie": Object,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .card {

        .poster, h3, p {
            width: 100%;
            color: white;
        }

        .poster {
            height: 300px;
            object-fit: contain;
            
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
    }
</style>