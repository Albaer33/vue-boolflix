<template>
  <div id="app">
    <Header @searchedWord="searchResult"/>
    <main>
      <div class="film">
        <h2>Film: </h2>
        <Cardfilm v-for="(film, index) in filmArray" :key="index" :details="film"/>
      </div>
      <div class="series">
        <h2>TV shows: </h2>
        <Cardseries v-for="(series, index) in seriesArray" :key="index" :details="series"/>
      </div>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Cardfilm from './components/Cardfilm.vue';
import Cardseries from './components/Cardseries.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Cardfilm,
    Cardseries
  },
  data: function() {
    return {
      apikey: '62bbed7da31113bfdbc2205370dfec35',
      filmArray: [],
      seriesArray: []
      }
    },
  methods: {
    searchResult: function(typedKeyword) {
      this.searchFilm(typedKeyword);
      this.searchSeries(typedKeyword);
    },
    // restituisce un array di oggetti di film
    searchFilm: function(typedKeyword) {
      axios.get('https://api.themoviedb.org/3/search/movie',
      {
      params: {
        api_key: this.apikey,
        query: typedKeyword,
      }
      })
      .then((response) => {
        this.filmArray = response.data.results;
      });
    },

    // restituisce un array di oggetti di serie tv
    searchSeries: function(typedKeyword) {
      axios.get('https://api.themoviedb.org/3/search/tv',
      {
      params: {
        api_key: this.apikey,
        query: typedKeyword,
      }
      })
      .then((response) => {
        this.seriesArray = response.data.results;
      });
    }
  },
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
main {
    width: 100%;
    padding: 20px;
    background-color: lightgray;
}
</style>
