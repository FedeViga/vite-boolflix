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
    <section>
        <div class="container">

            <div id="movies-list">

                <MovieItem 
                    v-for="currentMovie in store.moviesList"
                    :movie ="currentMovie"
                ></MovieItem>

            </div>
        </div>
    </section>
</template>

<style lang="scss">

section {
    height: calc(100vh - 72px);
    overflow: auto;

    #movies-list {
        display: flex;
        flex-direction: column;
        gap: 20px;
        padding: 20px 0px;
    }
    
    .info {
        margin-left: 20px;
    }
}


</style>