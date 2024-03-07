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
    <div class="container">

      <img src="https://fontmeme.com/permalink/240306/a1497229f7b7e248527b4619e155203f.png" alt="boolflix logo">
  
      <div class="search">
        <input type="search" placeholder="Search Movie" v-model="store.title">
        <button @click="$emit('search')">Search</button>
      </div>
    </div>

  </nav>

</template>

<style lang="scss">

  nav {
    background-color: black;

    .container {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0;

      img {
        margin-top: 5px;
        height: 60px;
      }

      .search {
        display: flex;
        gap: 10px;
        margin-right: 10px;
      }
  
      input {
        padding: 0px 10px;
      }
  
      button {
        padding: 5px 10px;
      }
    }


  }
</style>