<template>
  <div id="app">
    <Header @searchedWord="searchFilm"/>
    <main>
      <Card v-for="(film, index) in filmArray" :key="index" :details="film"/>
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
    Card,
  },
  data: function() {
    return {
      typedKeyword: '',
      filmArray: [],
      }
    },
  methods: {
    searchFilm: function(typedKeyword) {
      axios.get('https://api.themoviedb.org/3/search/movie',
      {
      params: {
        api_key: '62bbed7da31113bfdbc2205370dfec35',
        query: typedKeyword,
      }
      })
      .then((response) => {
        this.filmArray = response.data.results;
      });
    },
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
