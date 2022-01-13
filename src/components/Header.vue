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
    height: 80px;
    line-height: 80px;
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
        border-color: lightgrey;
        width: 200px;
        padding: 5px;
        margin: 0 20px;
        background-color: black;
    }
    button {
        border-radius: 5px;
        color: white;
        padding: 5px 15px;
        background-color: #9c050d;
    }
}
</style>