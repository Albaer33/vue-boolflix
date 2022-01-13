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
        border-color: white;
        outline: none;
        width: 300px;
        padding: 9px;
        margin: 0 20px;
        background-color: black;
    }
    button {
        border: none;
        border-radius: 3px;
        color: white;
        padding: 10px 20px;
        text-align: center;
        text-decoration: none;
        font-size: 16px;
        background-color: #9c050d;
    }
    button:hover {
        background-color: #a83339;
        cursor: pointer;
    }
}
</style>