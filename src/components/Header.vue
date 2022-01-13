<template>
    <header>
        <div class="logo">BOOLFLIX</div>
        <div class="searchform">
            <input v-model="searchWord" type="text" placeholder="Digita un film o una serie tv">
            <button @click="$emit('searchedWord', searchWord)">Cerca</button>
        </div>
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
    height: 100px;
    line-height: 100px;
    padding: 0 50px;
    background-color: black;
    display: flex;
    justify-content: space-between;
    .logo {
        font-size: 30px;
        color: #E50914;
    }
    input {
        color: inherit;
        width: 200px;
        padding: 5px;
        margin: 0 20px;
        background-color: black;
    }
    button {
        color: white;
        padding: 5px;
        background-color: #9c050d;
    }
}
</style>