<template>
  <div class="main">
      <section>
        <video width="960" height="720" autoplay muted controls src="../assets/Dark_trailer.mp4"
        type="Dark_trailer/mp4">
        </video>
      </section>
      <section v-if="!searched">
        <h2>Film Popolari</h2>
        <div class="movies">
            <Card 
            v-for= "popFilm in popFilms"
            :key= "popFilm.id"
            :item= "popFilm"
            />
        </div>
        <h2>Serie TV Popolari</h2>
        <div class="movies">
            <Card 
            v-for= "popTVserie in popTVseries"
            :key= "popTVserie.id"
            :item= "popTVserie"
            />
        </div>
      </section>
      <section v-else>
        <div v-if="films.length > 0" class="">
            <h2>films</h2>
            <div class="movies">
                <Card 
                v-for= "film in films"
                :key = "film.id"
                :item = "film"
                />
            </div>
        </div>
        <div v-if="films.length > 0" class="movies-container">
            <h2>TV Series</h2>
            <div class="series">
                <Card 
                v-for="tv_serie in tv_series"
                :key = "tv_serie.id"
                :item = "tv_serie"
                />
            </div>
        </div>
      <h1 v-else>La tua ricerca non ha prodotto risultati</h1>
      </section>
  </div>
</template>

<script>
import Card from './Card.vue'

export default {
    name: 'Main',

    props: {
        "films": Array,
        "tv_series": Array,
        "popFilms": Array,
        "popTVseries": Array,
        "searched": Boolean
    },

    components: {
        Card
    }
}
</script>

<style scoped>
.main {
    height: 100vh;
    width: 100%;
    background-color: black;
    overflow-y: scroll;
}

.movies,
.series {
    display: flex;
    align-content: flex-start;
    overflow-x: auto;
    margin: 10px 0;
}

h2 {
    text-transform: uppercase;
    font-size: 28px;
    margin: 20px 5px 15px;
    color: white;
}

::-webkit-scrollbar {
    height: 8px;
    width: 10px;
    cursor: pointer;
}

::-webkit-scrollbar-thumb {
    background: rgb(187, 187, 187);
    border-radius: calc(15px / 2);
    cursor: pointer;
}
::-webkit-scrollbar-thumb:hover {
    background: red;
}

video {
    width: 100%;
    object-fit: cover;
}

</style>