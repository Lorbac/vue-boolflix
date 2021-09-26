<template>

<div class="card">
    <h3>{{ movie.title }}</h3>
    <p>Titolo originale: {{ movie.original_title }}</p>
    <p>Lingua: {{ movie.original_language }}</p>
    <p>Media voti: {{ movie.vote_average }}</p>
</div>

</template>

<script>
export default {
  name: 'Card',
  props: {
      "movie": Object,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .card {
        p {
            font-size: 12px;
        }
    }
</style>