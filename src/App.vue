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
    axios.get('https://api.themoviedb.org/3/movie/popular?api_key=e99307154c6dfb0b4750f6603256716d').then(result => {
      this.store.moviesList = result.data.results.slice(0, 10);
      this.store.moviesList;
      console.log(this.store.moviesList);
    })

    axios.get('https://api.themoviedb.org/3/tv/popular?api_key=e99307154c6dfb0b4750f6603256716d').then(result => {
      this.store.seriesList = result.data.results.slice(0, 10);
      console.log(this.store.seriesList);
    })
  },

  methods: {
    // metodo per fare chiamata axios e salvare i risultati nell'array movieslist nello store
    searchmovie() {
      this.store.search = true;
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=' + this.store.title).then(result => {
        this.store.moviesList = result.data.results;
        console.log(this.store.moviesList);
      })
    },

    // metodo per fare chiamata axios e salvare i risultati nell'array serieslist nello store
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