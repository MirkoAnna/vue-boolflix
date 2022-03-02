<template>
    <div class="container">
        <div class="logo">
            <h1>
                Boolflix
            </h1>
        </div>
        <form action="">
            <input type="text" placeholder="Cerca Film o serie TV" v-model="searchText" @keyup="$emit('search', searchText)">
        </form>
    </div>
</template>

<script>
export default {
    name:'MyHeader',
    data() {
        return {
            searchText: ''
        }
    }
}
</script>

<style lang="scss" scoped>
    .container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1%;
        width: 100%;
        height: 12vh;
        background-color: black;

        h1 {
            color: red;
            text-transform: uppercase;
            font-size: 160%;
            font-weight: bold;
        }
    }
</style>