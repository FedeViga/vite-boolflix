<script>

import {store} from '../js/store.js'

export default {

    name: 'AppMovies',

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
                <div class="movie" v-for="currentMovie in store.moviesList">
                    <h2>
                        {{ currentMovie.title }}
                    </h2>

                    <h3>
                        {{ currentMovie.original_title }}
                    </h3>
                    <h3>
                        {{ currentMovie.original_language }}
                    </h3>
                    <h3>
                        {{ currentMovie.vote_average }}
                    </h3>

                </div>
            </div>
        </div>
    </section>
</template>

<style lang="scss">

</style>