<script>
import axios from 'axios';
import {store} from '../js/store.js';
export default {

    name: 'CardItem',

    props: {
        card: Object,
    },

  data() {
    return {
        store,
    }
  }, 

  methods: {
    // metodo per visualizzare in pagina la bandiera corrispondente alla lingua del film o serie
    getFlag() {
        let flag = this.card.original_language;
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
        if (flag == 'hi') {
            flag = 'in'
        }

        return flag
    },

    // metodo per convertire il voto in numero intero da 1 a 5
    roundVote() {

        let roundedVote = this.card.vote_average / 2;

        if(roundedVote % 1 <= 0.4) {

            roundedVote = Math.floor(roundedVote)

        } else {

            roundedVote = Math.ceil(roundedVote)
        }

        return roundedVote
    },

    // metodo per ottenere i primi 5 attori del cast
    getCast() {
        // per film
        if(this.card.title) {

            axios.get('https://api.themoviedb.org/3/movie/' + this.card.id + '/casts?api_key=e99307154c6dfb0b4750f6603256716d').then(result => {
                this.store.actors = result.data.cast.slice(0, 5);
                console.log('attori',this.store.actors);
          })
        // per serie tv
        } else {
            axios.get('https://api.themoviedb.org/3/tv/' + this.card.id + '/aggregate_credits?api_key=e99307154c6dfb0b4750f6603256716d').then(result => {
                this.store.actors = result.data.cast.slice(0, 5)
          })
        }
    },

    clearActors() {
        this.store.actors = [];
    }
  }
}
</script>


<template>

    <div class=" px-5 px-sm-1 position-relative" @mouseleave="clearActors()">

        <img 
            v-if="card.poster_path" 
            class="w-100 h-100" 
            :src="'https://image.tmdb.org/t/p/w342' + card.poster_path"
        >

        <div 
            v-else 
            class="d-flex justify-content-center align-items-center bg-black h-100"
        >
            COPERTINA NON DISPONIBILE
        </div>

        
        <div class="position-absolute top-0 start-0 w-100 h-100 px-5 px-sm-1">

            <div class="info h-100 p-2 overflow-auto">

                <h3 
                    v-if="card.title"
                    class="title text-center py-2" 
                >
                    {{ card.title }}
                </h3>
                
                <h3 
                    v-else
                    class="title text-center py-2" 
                >
                    {{card.name}}
                </h3>

                <h3 
                    v-if="card.original_title"
                    class="description" 
                >
                    Titolo originale : {{ card.original_title }}
                </h3>
    
                <h3 
                    v-else
                    class="description" 
                >
                    Titolo originale : {{ card.original_name }}
                </h3>
    
                <h3 class="description">
                    Lingua originale : 
                    <img
                        :src="'https://flagcdn.com/16x12/' + getFlag() + '.png'"
                        width="20"
                        height="15"
                        :alt="getFlag()"
                    >
                </h3>

                <h3 class="description">
                    Media voto : 
                    <i 
                        v-for="n in roundVote()" 
                        :key="n" 
                        class="fa-solid fa-star"
                    ></i>
                    <i 
                        v-for="n in 5 - roundVote()" 
                        :key="n" 
                        class="fa-regular fa-star"
                    ></i>
                </h3>

                <button 
                    type="button" 
                    class="btn btn-sm btn-danger me-1"
                    @click="getCast()"
                >
                    Cast
                </button>

                <span v-for="currentActor in this.store.actors">
                    {{ currentActor.name }},
                </span>

                <p class="overflow-auto">
                    <strong>Overview:</strong> {{ card.overview }}
                </p>
            </div>


        </div>

    </div>

</template>

<style lang="scss">

    .info {
        opacity: 0;
        background-color: rgba(0, 0, 0, 0.801);
        transition: .3s ease;

        &:hover {
            opacity: 1;
        }

        .title {
            font-size: 2.2em;
        }

        .description {
            font-size: 1.4em;
        }
    }

    @media screen and (min-width:576px) {
        .info {
            .title {
                font-size: 1.5em;
            }
            .description {
            font-size: 1em;
        }
        }
    }


</style>