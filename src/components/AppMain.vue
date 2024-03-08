<script>
import AppCards from './AppCards.vue'
export default {

    name: 'AppMain',

    components: {
        AppCards,
    }
}
</script>


<template>

    <main>
        <AppCards></AppCards>
    </main>

</template>

<style lang="scss">

    main {
        height: calc(100vh - 72px);
        overflow: auto;
    }
</style>