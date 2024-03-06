<script>

import {store} from '../js/store.js'
export default {

    name: 'AppNav',

  data() {
    return {
      store,
    }
  }
}
</script>


<template>

  <nav>

    <img src="https://fontmeme.com/permalink/240306/a1497229f7b7e248527b4619e155203f.png" alt="boolflix logo">

    <div class="search">
      <input type="search" placeholder="Search Movie" v-model="store.movieTitle">
      <button @click="$emit('search')">Search</button>
    </div>

  </nav>
</template>

<style lang="scss">

  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: black;
    padding: 0px 40px;

    .search {
      display: flex;
      gap: 10px;
    }

    input {
      padding-left: 10px;
    }

    button {
      padding: 5px 10px;
    }

  }
</style>