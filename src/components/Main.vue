<template>
  <div class="main">
      <section v-if="cards.length > 0" class="movies-container">
          <h2>films</h2>
          <div class="movies">
            <Card 
            v-for="card in cards"
            :key = "card.id"
            :item = "card"
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
        "cards": Array
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

.movies {
    display: flex;
    align-content: flex-start;
    flex-wrap: wrap;
}

</style>