<template>
  <div class="card">
  <h3> {{ item.title }} </h3>
  <h4> {{ item.original_title }} </h4>
  <p v-if="item.original_language == 'en'"> <img src="../assets/en.png" alt=""> </p>
  <p v-else-if="item.original_language == 'it'"> <img src="../assets/it.png" alt=""> </p>
  <p v-else> {{item.original_language}} </p>
  <p> {{ item.vote_average }}</p>
  </div>
</template>

<script>

export default {
    name: 'Card',

    props: {
        "item": Object
    },
}
</script>

<style scoped>

.card {
    height: 200px;
    width: 120px;
    margin: 5px;
    border: 2px solid blue;
}

h2 {
    font-size: 14px;
    text-align: center;
}

img {
  height: 12px;
  width: 20px;
}
</style>