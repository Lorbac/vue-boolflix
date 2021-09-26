<template>
    <div class="container">
          <Card :movies="movies" :APIquery="APIquery"/>
    </div>
</template>

<script>
import Card from "../components/Card.vue"

export default {
  name: 'Main',
  props: {
   "movies": Array,
   "APIquery": String,
  },
  components: {
    Card,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
