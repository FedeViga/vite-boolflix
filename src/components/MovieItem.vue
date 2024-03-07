<script>

export default {

    name: 'MovieItem',

    props: {
        movie: Object,
    },

  data() {
    return {
    }
  }
}
</script>


<template>

    <div class="movie">

        <h2>
            {{ movie.title }}
        </h2>
        <div class="info">

            <h3>
                Titolo originale : {{ movie.original_title }}
            </h3>
            <h3>
                Lingua originale : {{ movie.original_language }}
            </h3>
            <h3>
                Media voto : {{ movie.vote_average }}
            </h3>

        </div>

    </div>

</template>

<style lang="scss">

</style>