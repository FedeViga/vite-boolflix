<script>

import {store} from '../js/store.js';
import CardItem from './CardItem.vue';

export default {

    name: 'AppCards',

    components: {
        CardItem,
    },

  data() {
    return {
      store,
    }
  }
}
</script>


<template>
    <section class="mt-3" v-if="store.moviesList.length > 0">
        <div class="container">

            <h2 class="text-center">
                Movies
            </h2>

            <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xxl-5 row-gap-3 my-3">

                <CardItem 
                    v-for="currentMovie in store.moviesList"
                    :card ="currentMovie"
                ></CardItem>

            </div>
        </div>
    </section>

    <section v-if="store.seriesList.length > 0">
        <div class="container">

            <h2 class="text-center">
                Series
            </h2>

            <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xxl-5 row-gap-3 my-3">

                <CardItem 
                    v-for="currentSerie in store.seriesList"
                    :card ="currentSerie"
                ></CardItem>

            </div>
        </div>
    </section>
</template>

<style lang="scss">

</style>