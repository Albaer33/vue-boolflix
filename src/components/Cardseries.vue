<template>
    <div class="card-wrapper">
        <h3 class="title">{{details.name}}</h3>
        <div class="original-title">Titolo originale: {{details.original_name}}</div>
        
        <div class="lg">
            <span>lingua originale: </span>
            <img
            class="flag-img" 
            v-if="details.original_language == 'it' || details.original_language == 'en'" 
            :src="require('../assets/img/flag-' + details.original_language + '.png')" alt="">
            <span v-else>{{details.original_language}}</span>
        </div>
        
        <div class="vote">voto medio: {{details.vote_average}}</div>
    </div>
</template>

<script>
export default {
    name: 'Cardseries',
    props: {
        details: Object
    },
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