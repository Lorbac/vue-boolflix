<template>
<div class="card">
    <div class="card-movie" v-if="movie.title">
        <h3>{{ movie.title }}</h3>
        <p>Titolo originale: {{ movie.original_title }}</p>
        <img :src="require(`../assets/${movie.original_language}.png`)" alt="">
        <p>Media voti: {{ movie.vote_average }}</p>
    </div>

    <div class="card-series" v-else>
        <h3>{{ movie.name }}</h3>
        <p>Titolo originale: {{ movie.original_name }}</p>
        <img :src="require(`../assets/${movie.original_language}.png`)" alt="">
        <p>Media voti: {{ movie.vote_average }}</p>
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
    img {
        width: 5%;
    }
</style>