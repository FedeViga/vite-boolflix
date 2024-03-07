<script>
import axios from 'axios';
import {store} from './js/store';

import AppNav from './components/AppNav.vue';
import AppMain from './components/AppMain.vue';

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
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=' + this.store.title).then(result => {
        this.store.moviesList = result.data.results;
        console.log(this.store.moviesList);
      })
    },

    searchserie() {
      axios.get('https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&query=' + this.store.title).then(result => {
        this.store.seriesList = result.data.results;
        console.log(this.store.seriesList);
      })
    }
  },

  components: {
    AppNav,
    AppMain
  }
}
</script>


<template>

  <AppNav @search="searchmovie(), searchserie()"></AppNav>
  <AppMain></AppMain>

</template>

<style lang="scss">

@use './styles/general' as *;

</style>