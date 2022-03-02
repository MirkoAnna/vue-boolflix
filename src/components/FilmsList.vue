<template>
    <div>
        <h2>Film</h2>
        <ul>
            <MyCard v-for="(film, index) in films" :key="index" :info='film' />  
        </ul>
    </div>
</template>

<script>
import MyCard from './partials/MyCard.vue';

export default {
    name: 'FilmsList',
    props: {
        'films': Array
    },
    components: {
        MyCard
    }
}
</script>

<style lang="scss" scoped>

    h2 {
        margin: 3% 0;
    }
    ul {
        display: flex;
        flex-wrap: wrap;
    }
</style>