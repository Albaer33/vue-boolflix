<template>
    <header>
        <input v-model="searchWord" type="text">
        <button @click="$emit('searchedWord', searchWord)">Cerca</button>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data: function() {
        return {
            searchWord: ''
        }
    }
}
</script>

<style scoped lang='scss'>
header {
    width: 100%;
    height: 80px;
    padding: 20px;
    background-color: pink;
}
</style>