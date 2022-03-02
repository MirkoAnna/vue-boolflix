<template>
    <div class="container">
        <h2>SerieTv</h2>
        <ul>
            <MyCard v-for="(serie, index) in series" :key="index" :info='serie' />  
        </ul>
    </div>
</template>

<script>
import MyCard from './partials/MyCard.vue';

export default {
    name: 'SeriesList',
    props: {
        'series': Array
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