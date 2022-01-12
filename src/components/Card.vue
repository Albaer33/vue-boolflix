<template>
    <div class="card-wrapper">
        <h3 class="title">{{details.title}}</h3>
        <div class="original-title">Titolo originale: {{details.original_title}}</div>
        <div class="lg">lingua originale: {{details.original_language}}</div>
        <div class="vote">voto medio: {{details.vote_average}}</div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        details: Object
    }
}
</script>

<style scoped lang='scss'>
.card-wrapper {
    padding: 20px;
}
</style>