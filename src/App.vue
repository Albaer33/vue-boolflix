<template>
  <div id="app">

    <Header @searchedWord="searchResult"/>

    <main>

      <h2>Film</h2>
      <div class="film">
        <Card v-for="(film, index) in filmArray" :key="index" :details="film"/>
      </div>

      <h2>TV shows</h2>
      <div class="series">
        <Card v-for="(series, index) in seriesArray" :key="index" :details="series"/>
      </div>
    </main>

  </div>
</template>

<script>
import Header from './components/Header.vue';
import Card from './components/Card.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Card
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
@import './style/general.scss';

main {
    height: calc(100vh - 80px);
    padding: 20px;
    background-color: #434343;
    h2 {
      margin: 25px 50px;
      font-size: 30px;
    }
    .film, .series{
      height: max-content;
      display: flex;
      overflow-x: auto;
      overflow-y: hidden;
    }
}
</style>
