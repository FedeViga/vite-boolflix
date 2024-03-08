<script>

import {store} from '../js/store.js';
import MovieItem from './MovieItem.vue';

export default {

    name: 'AppMovies',

    components: {
        MovieItem,
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

                <MovieItem 
                    v-for="currentMovie in store.moviesList"
                    :movie ="currentMovie"
                ></MovieItem>

            </div>
        </div>
    </section>

    <section v-if="store.moviesList.length > 0">
        <div class="container">

            <h2>
                Series:
            </h2>

            <div class="cards-list">

                <MovieItem 
                    v-for="currentSerie in store.seriesList"
                    :movie ="currentSerie"
                ></MovieItem>

            </div>
        </div>
    </section>
</template>

<style lang="scss">

</style>