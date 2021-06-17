<template>
  <div class="main">
      <section v-if="films.length > 0" class="movies-container">
          <h2>films</h2>
          <div class="movies">
            <Card 
            v-for="film in films"
            :key = "film.id"
            :item = "film"
            />
          </div>
      </section>
      <section v-if="films.length > 0" class="movies-container">
          <h2>TV Series</h2>
          <div class="series">
            <Card 
            v-for="tv_serie in tv_series"
            :key = "tv_serie.id"
            :item = "tv_serie"
            />
          </div>
      </section>
      <h1 v-else>La tua ricerca non ha prodotto risultati</h1>
  </div>
</template>

<script>
import Card from './Card.vue'

export default {
    name: 'Main',

    props: {
        "films": Array,
        "tv_series": Array
    },

    components: {
        Card
    }
}
</script>

<style scoped>
.main {
    height: calc(100vh - 100px);
    width: 100%;
    background-color: lightgrey;
}

.movies,
.series {
    display: flex;
    align-content: flex-start;
    flex-wrap: wrap;
}

</style>