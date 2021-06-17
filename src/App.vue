<template>
  <div id="app">
    <Header @actionSearch="search" />
    <Main
    :films="movies"
    :tv_series="series"
    :popFilms="popularMovies"
    :popTVseries="popularSeries"
    :searched="searched"
     />
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
      apiPopularMoviesUrl:'https://api.themoviedb.org/3/movie/popular',
      apiPopularSeriesUrl:'https://api.themoviedb.org/3/tv/popular',
      apiKey: '5712408c7a8f4a15ddd3839746e949f2',

      movies: [],
      series: [],
      popularMovies: [],
      popularSeries: [],
      searched: false,
    }
  },

  created() {
    const self = this;
    const getPopularMovies = axios.get(self.apiPopularMoviesUrl, {
            params: {
              api_key: self.apiKey,
              language: 'it-IT'
            }
          });

      const getPopularSeries = axios.get(self.apiPopularSeriesUrl, {
          params: {
            api_key: self.apiKey,
            language: 'it-IT'
          }
        });
        
      Promise.all([getPopularMovies, getPopularSeries]).then((res) => {
                self.popularMovies = res[0].data.results;
                self.popularSeries = res[1].data.results;
            });
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
                this.searched = true;
            });
    }
  }
}

</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.min.css';
@import "~@fontsource/lato/400.css";

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Lato', sans-serif;
}


</style>