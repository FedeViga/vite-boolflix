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

  <nav class="bg-black py-2 py-sm-0">
    <div class="container d-flex flex-column flex-sm-row justify-content-center justify-content-sm-between align-items-center">

      <img src="https://fontmeme.com/permalink/240306/a1497229f7b7e248527b4619e155203f.png" alt="boolflix logo">
  
      <div class="d-flex gap-2">
        <div class="input-group mb-2 mb-sm-0">
          <input type="search" class="form-control" placeholder="Search Movie or Serie" aria-label="Recipient's username" aria-describedby="button-addon2" v-model="store.title">
          <button class="btn btn-danger" type="button" id="button-addon2" @click="$emit('search')">Search</button>
        </div>
      </div>

    </div>

  </nav>

</template>

<style lang="scss">

</style>