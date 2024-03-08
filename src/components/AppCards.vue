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
    <section v-if="store.moviesList.length > 0">
        <div class="container">

            <h2>
                Movies:
            </h2>

            <div class="cards-list">

                <CardItem 
                    v-for="currentMovie in store.moviesList"
                    :card ="currentMovie"
                ></CardItem>

            </div>
        </div>
    </section>

    <section v-if="store.seriesList.length > 0">
        <div class="container">

            <h2>
                Series:
            </h2>

            <div class="cards-list">

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