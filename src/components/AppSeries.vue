<script>

import {store} from '../js/store.js';
import SerieItem from './SerieItem.vue';

export default {

    name: 'AppSeries',

    components: {
        SerieItem,
    },

  data() {
    return {
      store,
    }
  }
}
</script>


<template>
    <section v-if="store.seriesList.length > 0">
        <div class="container">

            <h2>
                Series:
            </h2>

            <div class="cards-list">

                <SerieItem 
                    v-for="currentSerie in store.seriesList"
                    :serie ="currentSerie"
                ></SerieItem>

            </div>
        </div>
    </section>
</template>

<style lang="scss">

</style>