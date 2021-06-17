<template>
  <div class="header">
      <div class="header-left">
        <img class="img-logo-container" src="../assets/logo_netflix.png" alt="">
        <p class="header_actions">
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
        placeholder="cerca"
        @keyup.enter="$emit('actionSearch', keywords)"
        >
        <i class="fas fa-search find" @click ="$emit('actionSearch', keywords)"></i>
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
        width: 45%;
    }

    .header-right {
        display: flex;
        align-items: center;
        margin-right: 50px;
    }

    input {
        height: 25px;
        margin-right: 30px;
        padding-left: 5px;
        border-radius: 10px;
    }

    span {
        color: white;
        margin: 0 10px;
        cursor: pointer;
    }

    .img-logo-container {
        width: 232px;
        margin-left: 5%;
        cursor: pointer;
    }

    .find {
        font-size: 22px;
        color: white;
        margin-right: 10px;
        margin-left: 5px;
        cursor: pointer;
    }

    @media screen and (max-width: 1500px) {
    .header_actions {
        display: none;
    }
    
}

    @media screen and (max-width: 500px) {
        .img-logo-container {
            width: 100px;
        }
    }

    @media screen and (max-width: 600px) {
        .header-right {
            display: flex;
            margin-right: 15px;
        }
        input {
            margin-right: 5px;
        }
    }
    
</style>