<template>
  <div class="card">
    <div class="image">
      <img :src="imgUrl + item.poster_path" alt="" v-if="item.poster_path">
      <img src="../assets/not_found.png" alt="Image not found" v-else>
      <!-- <div class="description">
        <h3> {{ item.title ? item.title : item.name }} </h3>
        <h4> {{ item.original_title ? item.original_title : item.original_name }} </h4>
        <p v-if="item.original_language == 'en'"> <img class="flag" src="../assets/en.png" alt=""> </p>
        <p v-else-if="item.original_language == 'it'"> <img class="flag" src="../assets/it.png" alt=""> </p>
        <p v-else> {{item.original_language}} </p>
      </div> -->
    </div>
        <p>Voto:</p> 
        <p>
          <span
          v-for="star in 5"
          :key="star"
          :class="star <= getAverage ? 'fas fa-star' : 'far fa-star'">
          </span>
        </p>
        <p> {{ getAverage }}</p>
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
      }
    },
    computed: {
      getAverage() {
        return Math.round(Math.round(this.item.vote_average) / 2)
      }
    }
}
</script>

<style scoped>

.card {
  height: 204px;
  width: 124px;
  margin: 2px;
  border: 2px solid blue;
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
  height: 200px;
  width: 120px;
}

/* span {
  display: inline-block;
  border: 1px solid red;
} */

.fa-star {
  height: 20px;
  width: 20px;
  color: white;
}


</style>