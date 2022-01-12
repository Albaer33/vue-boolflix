<template>
    <div class="card-wrapper">
        <img :src="`https://image.tmdb.org/t/p/w342${details.poster_path}`" alt="">
        <h3 class="title">{{details.title}}</h3>
        <div class="original-title">Titolo originale: {{details.original_title}}</div>
        
        <div class="lg">
            <span>lingua originale: </span>
            <img
            class="flag-img" 
            v-if="details.original_language == 'it' || details.original_language == 'en'" 
            :src="require('../assets/img/flag-' + details.original_language + '.png')" alt="">
            <span v-else>{{details.original_language}}</span>
        </div>
        
        <div class="vote">
            voto medio: 
            <!-- stelle piene -->
            <i v-for="(star, i) in voteStar" :key="i" class="fas fa-star"></i>
            <!-- stelle vuote -->
            <i v-for="(star, j) in (5 - voteStar)" :key="j" class="far fa-star"></i>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Filmcard',
    props: {
        details: Object
    },
    data: function() {
        return {
            voteStar: Math.round(this.details.vote_average / 2)
        }
    }
}
</script>

<style scoped lang='scss'>
.card-wrapper {
    padding: 20px;
}
.flag-img {
    width: 20px;
    height: 15px;
}
</style>