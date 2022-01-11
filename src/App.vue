<template>
  <div id="app">
    <Header/>
    <main>
      <Card/>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Card from './components/Card.vue'

export default {
  name: 'App',
  components: {
    Header,
    Card
  }
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
