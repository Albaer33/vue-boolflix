<template>
    <main>
        <Card/>
    </main>
</template>

<script>
import Card from './Card.vue'
import axios from 'axios';

export default {
    components: {
        Card
    },
    name: 'Cardlist',
    data: function() {
        return {
            searchedWord: 'vita',
            filmArray: [],
        }
    },
    created: function() {
        axios.get('https://api.themoviedb.org/3/search/movie',
        {
            params: {
                api_key: '62bbed7da31113bfdbc2205370dfec35',
                query: searchedWord,
            }
        })
        .then((response) => {
            this.filmArray = response.data.response;
        });
    },
}
</script>

<style scoped lang='scss'>
main {
    width: 100%;
    padding: 20px;
    background-color: lightgray;
}
</style>