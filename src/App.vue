<template>
  <div id="app">
    <Header/>
    <Cardlist/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Cardlist from './components/Cardlist.vue'

export default {
  name: 'App',
  components: {
    Header,
    Cardlist,
  },
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
