<template>
<div class="flip-card">
    <div class="flip-card-inner" v-if="movie.title">
        <div class="flip-card-front">
            <img v-if="movie.poster_path" class="poster" :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" :alt="`${movie.title}`">
            <img class="poster" v-else src="../assets/not-found.png" alt="">
        </div>
        <div class="flip-card-back">
            <h3>{{ movie.title }}</h3>
            <p>Titolo originale: {{ movie.original_title }}</p>
            <p>Voto: <i v-for="i in 5" :key="i" class="fa-star" :class="(i <= getVote()) ? 'fas' : 'far'"></i></p>
            <img class="flags" :src="require(`../assets/${movie.original_language}.png`)" :alt="`${movie.original_language}`">
            <p class="overview">Trama: {{ movie.overview }}</p>
        </div>
    </div>

    <div class="flip-card-inner" v-else>
        <div class="flip-card-front">
            <img v-if="movie.poster_path" class="poster" :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" :alt="`${movie.name}`">
            <img class="poster" v-else src="../assets/not-found.png" alt="">
        </div>
        <div class="flip-card-back">
            <h3>{{ movie.name }}</h3>
            <p>Titolo originale: {{ movie.original_name }}</p>
            <p>Voto: <i v-for="i in 5" :key="i" class="fa-star" :class="(i <= getVote()) ? 'fas' : 'far'"></i></p>
            <img class="flags" :src="require(`../assets/${movie.original_language}.png`)" :alt="`${movie.original_language}`">
            <p class="overview">Trama: {{ movie.overview }}</p>
        </div>
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

    .flip-card {
        background-color: transparent;
        width: 300px;
        height: 450px;
        // perspective: 1000px;
    }

    .flip-card-inner {
        position: relative;
        width: 100%;
        height: 100%;
        text-align: center;
        transition: transform 0.6s;
        transform-style: preserve-3d;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    }

    .flip-card:hover .flip-card-inner {
        transform: rotateY(180deg);
    }

    .flip-card-front, .flip-card-back {
        position: absolute;
        width: 100%;
        height: 100%;
        -webkit-backface-visibility: hidden;
        backface-visibility: hidden;
    }

    .flip-card-front {
        background-color: #bbb;
        color: black;
    }

    .flip-card-back {
        background-color: black;
        color: white;
        transform: rotateY(180deg);
        display: flex;
        flex-direction: column;
        align-items: center;

        h3 {
            font-size: 14px;
            padding: 10px;
        }

        p {
            font-size: 12px;
            padding: 5px;
        }

        .flags {
            width: 5%;
        }

        i {
            color: yellow;
        }

        .overview {
            overflow-x: auto;
        }
    }
    
    .poster, h3, p, div {
        color: white;
    }

    .poster {
        width: 100%;
        height: 450px;
        object-fit:fill;
    }
</style>