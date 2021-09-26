<template>
    <ul v-if="APIquery !='' ">
        <li v-for="(movie, index) in movies" :key="index">
            <h3>{{ movie.title }}</h3>
            <p>Titolo originale: {{ movie.original_title }}</p>
            <p>Lingua: {{ movie.original_language }}</p>
            <p>Media voti: {{ movie.vote_average }}</p>
        </li>
    </ul>

    <h2 v-else>Inserisci una parola chiave nella ricerca</h2>
</template>

<script>
export default {
  name: 'Card',
  props: {
      "movies": Array,
      "APIquery": String,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    ul {
        list-style: none;

        li {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 10px;
        }
    }

    h2 {
        text-align: center;
        margin-top: 150px;
    }
</style>