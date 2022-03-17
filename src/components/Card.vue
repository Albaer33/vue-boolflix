<template>
    <div class="card-wrapper">
        <div class="poster-container">
            <img 
            v-if="details.poster_path" 
            class="poster" 
            :src="`https://image.tmdb.org/t/p/w342${details.poster_path}`" 
            alt="">
            <img class="noposter" v-else src="../assets/img/noimg.png" alt="">
        </div>

        <div class="product-info">
            <h3 v-if="details.title" class="title">{{details.title}}</h3>
            <h3 v-else class="title">{{details.name}}</h3>

            <div v-if="details.original_title" class="original-title">Titolo originale: {{details.original_title}}</div>
            <div v-else class="original-title">Titolo originale: {{details.original_name}}</div>
            
            <div class="lg">
                <span>lingua originale: </span>
                <img
                class="flag-img" 
                v-if="details.original_language == 'it' || details.original_language == 'en'" 
                :src="require('../assets/img/flag-' + details.original_language + '.png')" alt="">
                <span v-else>{{details.original_language}}</span>
            </div>
            
            <!-- <div class="vote">
                <span>voto medio:</span>
                <span v-for="(star, index) in 5" :key="index">
                    
                    <i class="fas fa-star fullStar"></i>
                    
                    <i class="far fa-star emptyStar"></i>
                </span>
            </div> -->

            <div class="overview">
                <span>Overview:</span>
                <div>{{details.overview}}</div>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    name: 'Card',
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
    margin: 0 15px;
    height: 300px;
    position: relative;
    box-shadow: 8px 12px 15px 5px #151515;
    cursor: pointer;
    .poster {
        position: relative;
        z-index: 1;
        height: 300px;
    }
    .noposter {
        height: 300px;
        width: 200px;
        visibility: hidden;
    }
    .product-info {
        width: 100%;
        padding: 15px;
        height: 300px;
        font-size: 12px;
        max-height: 100%;
        position: absolute;
        top: 5px;
        left: 50%;
        transform: translate(-50%);
        .title {
            font-size: 16px;
        }
        .lg {
            .flag-img {
                width: 15px;
                height: 10px;
            }
        }
        .overview {
            padding: 5px 0;
            overflow: hidden;
            max-height: 140px;
        }
    }
}
.card-wrapper:hover .poster {
    visibility: hidden;
}
.fullStar {
    color: goldenrod;
}
</style>