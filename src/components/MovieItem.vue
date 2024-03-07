<script>

export default {

    name: 'MovieItem',

    props: {
        movie: Object,
    },

  data() {
    return {
    }
  }, 

  methods: {
    getMoviesFlag() {
        let flag = this.movie.original_language;
        if (flag == 'en' || flag == 'uk') {
            flag = 'gb';
        }

        if (flag == 'zh') {
            flag = 'cn'
        }
        
        if (flag == 'ja') {
            flag = 'jp'
        }

        if (flag == 'ko') {
            flag = 'kr'
        }
        
        return flag
    }
  }
}
</script>


<template>

    <div class="card">

        <h2>
            {{ movie.title }}
        </h2>
        <div class="info">

            <h3>
                Titolo originale : {{ movie.original_title }}
            </h3>
            <h3>
                Lingua originale : <img
                                        :src="'https://flagcdn.com/16x12/' + getMoviesFlag() + '.png'"
                                        width="16"
                                        height="12"
                                        :alt="getMoviesFlag()">
            </h3>
            <h3>
                Media voto : {{ movie.vote_average }}
            </h3>

        </div>

    </div>

</template>

<style lang="scss">

</style>