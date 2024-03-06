<script>
import axios from 'axios';
import {store} from './js/store';

import AppNav from './components/AppNav.vue';
import AppMovies from './components/AppMovies.vue';

export default {

  data() {
    return {
      store,
    }
  },

  created() {

  },

  methods: {
    searchmovie() {
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=' + this.store.movieTitle).then(result => {
        this.store.moviesList = result.data.results;
        console.log(this.store.moviesList);
      })
    }
  },

  components: {
    AppNav,
    AppMovies
  }
}
</script>


<template>

  <AppNav @search="searchmovie()"></AppNav>
  <AppMovies></AppMovies>

</template>

<style lang="scss">

@use './styles/general' as *;

</style>