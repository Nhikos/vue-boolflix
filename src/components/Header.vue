<template>
  <div class="header">
      <span>ciao</span>
      <input
       v-model="keywords"
       type="text"
       placeholder="cerca un film"
       @keyup.enter="$emit('actionSearch', keywords)"
       >
      <button
      @click ="$emit('actionSearch', keywords)">Cerca</button>
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
        justify-content: space-between;
        align-items: center;
        height: 100px;
        width: 100%;
        background-color: lightsteelblue;
    }

    input {
        margin-right: 30px;
    }

    button {
        cursor: pointer;
    }
    
</style>