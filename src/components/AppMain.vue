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

    <main class="text-white">
        <AppCards></AppCards>
    </main>

</template>

<style lang="scss">

    main {
        height: calc(100vh - 72px);
        overflow: auto;
    }

    @media screen and (max-width: 576px){
        main{
            height: calc(100vh - 134px);
        }
        
    }
</style>