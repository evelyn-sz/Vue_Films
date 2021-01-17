<template lang="html">
    <div v-if="film" id="filmDetail">
        <div id="detailWrapper">
          <div>
            <h2>{{ film.title }}</h2>
            <button type="submit" id="button" v-on:click="addToFavourites">Add to favourite films</button>
          </div>
            <div id="flexWrapper">
                <div id="left">
                    <p><span>Director: </span>{{ film.director }}</p>
                    <p><span>Producer: </span>{{ film.producer }}</p>
                    <p><span>Release date: </span>{{ film.release_date }}</p>

                    <p><span>Characters: </span></p>
                        <ul :characters="characters" v-for="character in film.people">
                            <li>{{ character.name }} </li>
                        </ul>

                    <p><span>Species: </span></p>
                        <ul v-for="specie in film.species">
                            <li>{{ specie.name }} </li>
                        </ul>

                    <p><span>Locations: </span></p>
                        <ul v-for="location in film.locations">
                            <li>{{ location }} </li>
                        </ul>

                    <p><span>Vehicles: </span></p>
                        <ul v-for="vehicle in film.vehicles">
                            <li>{{ vehicle }} </li>
                        </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import { eventBus } from '../main.js';
export default {
    name: 'film-detail',
    // props: ['film'],
    data() {
        return {
            film: null,
            characters: [],
            species: []
        }
    },
    mounted() {
        eventBus.$on('film-selected', (film) => {
            this.film = film
        })
    },
    methods: {
      addToFavourites: function() {
        eventBus.$emit('film-favourite', this.film)
      }
    }
}
</script>

<style lang="css" scoped>
#detailWrapper {
  max-width: 500px;
}
</style>