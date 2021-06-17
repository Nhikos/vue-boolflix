<template>
  <div class="header">
      <div class="header-left">
        <img class="img-logo-container" src="../assets/logo_netflix.png" alt="">
        <p>
            <span>Home</span>
            <span>Serie TV</span>
            <span>Film</span>
            <span>Nuovi Arrivi</span>
            <span>La mia lista</span>
        </p>
      </div>
      <div class="header-right">
        <input
        v-model="keywords"
        type="text"
        placeholder="cerca un film"
        @keyup.enter="$emit('actionSearch', keywords)"
        >
      <button @click ="$emit('actionSearch', keywords)">Cerca</button>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Header',
    data:function () {
    return {
        keywords: '' 
        }
  },
}

</script>

<style scoped>
    .header {
        display: flex;
        position: fixed;
        justify-content: space-between;
        align-items: center;
        height: 100px;
        width: 100%;
        background-color: rgba(0, 0, 0, 0);
        z-index: 100;
    }

    .header-left {
        display: flex;
        align-items: center;
    }

    .header-right {
        display: flex;
        margin-right: 50px;
    }

    input {
        margin-right: 30px;
    }

    span {
        color: white;
        margin: 0 10px;
        cursor: pointer;
    }

    .img-logo-container {
        width: 190px;
        margin-left: 35px;
        cursor: pointer;
    }

    button {
        cursor: pointer;
    }
    
</style>