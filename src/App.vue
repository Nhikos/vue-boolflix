<template>
  <div id="app">
    <Header @actionSearch="search" />
    <Main :cards="movies" />
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',

  components: {
    Header,
    Main,
  },
  data: function(){
    return {
      apiMovieUrl:'https://api.themoviedb.org/3/search/movie',
      apiSeriesUrl:'https://api.themoviedb.org/3/search/tv',
      apiKey: '5712408c7a8f4a15ddd3839746e949f2',

      movies: [],
      series: [],
    }
  },
  methods: {
    search: function(text) {
      const getMovies = axios.get(this.apiMovieUrl, {
            params: {
              api_key: this.apiKey,
              query: text,
              language: 'it-IT'
            }
          });

      const getSeries = axios.get(this.apiSeriesUrl, {
          params: {
            api_key: this.apiKey,
            query: text,
            language: 'it-IT'
          }
        });
        
      Promise.all([getMovies, getSeries]).then((res) => {
                this.movies = res[0].data.results;
                this.series = res[1].data.results;
                console.log(res);
            });
    }
  }
}

</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}


</style>