<template>
  <div id="app">
    <Header/>
    <main>
      <Card/>
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
      searchedWord: 'ritorno al futuro',
      filmArray: [],
      }
    },
  created: function() {
    axios.get('https://api.themoviedb.org/3/search/movie',
    {
      params: {
        api_key: '62bbed7da31113bfdbc2205370dfec35',
        query: this.searchedWord,
      }
    })
    .then((response) => {
      this.filmArray = response.data.results;
    });
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
