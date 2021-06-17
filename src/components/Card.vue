<template>
  <div class="card" @mouseover="onHover" @mouseleave="onLeave">
      <img
       :src="imgUrl + item.poster_path" alt="Copertina" v-if="item.poster_path">
      <img src="../assets/not_found.png" alt="Image not found" v-else>
      <div class="description" v-if="showDescription">
        <h3> {{ item.title ? item.title : item.name }} </h3>
        <h4> {{ item.original_title ? item.original_title : item.original_name }} </h4>
        <p v-if="item.original_language == 'en'"> <img class="flag" src="../assets/en.png" alt=""> </p>
        <p v-else-if="item.original_language == 'it'"> <img class="flag" src="../assets/it.png" alt=""> </p>
        <p v-else> {{item.original_language}} </p>
        <p>Voto:</p> 
        <p>
          <span
          v-for="star in 5"
          :key="star"
          :class="star <= getAverage ? 'fas fa-star' : 'far fa-star'">
          </span>
        </p>
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
        // hover: false,
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

h2 {
  font-size: 14px;
  text-align: center;
}

.flag {
  height: 12px;
  width: 20px;
}

img {
      height: 250px;
    width: 170px;
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