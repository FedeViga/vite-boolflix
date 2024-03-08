<script>
import AppMovies from './AppMovies.vue'
export default {

    name: 'AppMain',

    components: {
        AppMovies,
    }
}
</script>


<template>

    <main>
        <AppMovies></AppMovies>
    </main>

</template>

<style lang="scss">

    main {
        height: calc(100vh - 72px);
        overflow: auto;
    }
</style>