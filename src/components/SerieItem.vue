<script>

export default {

    name: 'SerieItem',

    props: {
        serie: Object,
    },

  data() {
    return {
    }
  },

  methods: {
      getSeriesFlag() {
            let flag = this.serie.original_language;
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
            {{ serie.name }}
        </h2>
        <div class="info">

            <h3>
                Titolo originale : {{ serie.original_name }}
            </h3>
            <h3>
                Lingua originale : <img
                                        :src="'https://flagcdn.com/16x12/' + getSeriesFlag() + '.png'"
                                        width="16"
                                        height="12"
                                        :alt="getSeriesFlag()">
            </h3>
            <h3>
                Media voto : {{ serie.vote_average }}
            </h3>

        </div>

    </div>

</template>

<style lang="scss">

</style>