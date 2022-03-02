<template>
    <div class="container">
        <section class="films">
            <FilmsList :films='films'/>

        </section>
        <section class="series">
            <SeriesList :series='series'/>
        </section>
    </div>
</template>

<script>
import FilmsList from './FilmsList.vue';
import SeriesList from './SeriesList.vue';

export default {
    name:'MyMain',
    props: {
        'films': Array,
        'series': Array
    },
    components: {
        FilmsList,
        SeriesList
    }
}
</script>

<style lang="scss" scoped>
    .container {
        display: flex;
        flex-direction: column;
        width: 100%;
    }
    .films, .series {
        padding: 3%;
    }
</style>