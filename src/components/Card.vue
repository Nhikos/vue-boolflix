<template>
  <div class="card" @mouseover="onHover" @mouseleave="onLeave">
      <img
       :src="imgUrl + item.poster_path" alt="Copertina" v-if="item.poster_path">
      <img src="../assets/not_found.png" alt="Image not found" v-else>
      <div class="description" v-if="showDescription">
        <h2> {{ item.title ? item.title : item.name }} </h2>
        <h3> {{ item.original_title ? item.original_title : item.original_name }} </h3>
        <p class="flag_container" v-if="item.original_language == 'en'"> <img class="flag" src="../assets/en.png" alt=""> </p>
        <p class="flag_container" v-else-if="item.original_language == 'it'"> <img class="flag" src="../assets/it.png" alt=""> </p>
        <p class="flag_container" v-else>Lingua: {{item.original_language}} </p>
        <h4>Voto:</h4> 
        <p>
          <span
          v-for="star in 5"
          :key="star"
          :class="star <= getAverage ? 'fas fa-star' : 'far fa-star'">
          </span>
        </p>
        <h4>Trama:</h4>
        <div class="trama">
          <p> {{ item.overview}} </p>
        </div>
      </div>
  </div>
</template>

<script>

export default {
    name: 'Card',

    props: {
        "item": Object
    },

    data: function() {
      return {
        imgUrl: "https://image.tmdb.org/t/p/w342/",
        showDescription: false
      }
    },
    computed: {
      getAverage() {
        return Math.round(Math.round(this.item.vote_average) / 2)
      }
    },

    methods: {
      onHover: function() {
        this.showDescription = true;
      },
      onLeave: function() {
        this.showDescription = !this.showDescription;
      }
    }
}
</script>

<style scoped>

.card {
  position: relative;
}

.flag_container{
  display: flex;
  justify-content: flex-end;
}

.flag {
  right: 0;
  height: 12px;
  width: 20px;
}

img {
      height: 250px;
    width: 170px;
}

h2 {
  font-size: 18px;
}
h3 {
  font-size: 12px;
  margin-top: 5px;
  margin-bottom: 5px;
}
h4 {
  font-size: 10px;
  margin-top: 5px;
  margin-bottom: 5px;
}

.active {
  background-color: #7fffd4;
  cursor: pointer;
}

.image {
  display: inline-block;
  position: relative;
}

.description {
  position: absolute;
  top: 0;
  left: 0;
  height: 99%;
  width: 100%;
  padding: 6px;
  color: white;
  overflow-y: auto;
  background-color: black;
  cursor: pointer;
}


.fa-star {
  height: 20px;
  width: 20px;
  color: yellow;
}

.trama {
  font-size: 12px;
  background-color: rgba(255, 255, 255, 0.349);
  border-radius: 10px;
  overflow-y: auto;
}

::-webkit-scrollbar {
    width: 5px;
    cursor: pointer;
}

::-webkit-scrollbar-thumb {
    background: white;
    border-radius: calc(15px / 2);
    cursor: pointer;
}

</style>