<template>
    <div class="card-wrapper">
        <h3 class="title">{{details.title}}</h3>
        <div class="original-title">{{details.original_title}}</div>
        <div class="lg">{{details.original_language}}</div>
        <div class="vote">{{details.vote_average}}</div>
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