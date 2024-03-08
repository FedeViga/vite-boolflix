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
    getFlag() {
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
    },

    roundVote() {

        let roundedVote = this.movie.vote_average / 2;

        if(roundedVote % 1 <= 0.4) {

            roundedVote = Math.floor(roundedVote)

        } else {

            roundedVote = Math.ceil(roundedVote)
        }

        return roundedVote
    }
  }
}
</script>


<template>

    <div class="card">

        <img :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path">

        <h2 v-if="movie.title">
            {{ movie.title }}
        </h2>

        <h2 v-else>
            {{movie.name}}
        </h2>

        <div class="info">

            <h3 v-if="movie.original_title">
                Titolo originale : {{ movie.original_title }}
            </h3>

            <h3 v-else>
                Titolo originale : {{ movie.original_name }}
            </h3>

            <h3>
                Lingua originale : <img
                                        :src="'https://flagcdn.com/16x12/' + getFlag() + '.png'"
                                        width="16"
                                        height="12"
                                        :alt="getFlag()">
            </h3>
            <h3>
                Media voto : 
                <i v-for="n in roundVote()" :key="n" class="fa-solid fa-star"></i>
                <i v-for="n in 5 - roundVote()" :key="n" class="fa-regular fa-star"></i>
            </h3>

        </div>

    </div>

</template>

<style lang="scss">

</style>