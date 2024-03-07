<script>
import AppMovies from './AppMovies.vue'
import AppSeries from './AppSeries.vue'
export default {

    name: 'AppMain',

    components: {
        AppMovies,
        AppSeries,
    }
}
</script>


<template>

    <main>
        <AppMovies></AppMovies>
        <AppSeries></AppSeries>
    </main>

</template>

<style lang="scss">

    main {
        height: calc(100vh - 72px);
        overflow: auto;
    }
</style>