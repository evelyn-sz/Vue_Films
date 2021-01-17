<template lang="html">
  <div>
    <h1>Films</h1>
    <div id="body">
      <film-filter-form :films="films"/>
        <ul class="favouriteFilms">
          <h2 v-on:submit.prevent v-if="favouriteFilms[0]">Favourite films</h2>
          <li v-for="favouriteFilm in favouriteFilms">{{ favouriteFilm.title }}
            <button type="submit" v-on:click="removeFromFavourites">Remove</button>
          </li>
        </ul>
      <film-detail/>
    </div>
  </div>
</template>

<script>

import { eventBus } from './main.js'

import FilmFilterForm from './components/FilmFilterForm.vue';
import FilmDetail from './components/FilmDetail.vue';

export default {
  data() {
    return {
      films: [],
      favouriteFilm: {},
      favouriteFilms: []
    }
  },
  components: {
    "film-filter-form": FilmFilterForm,
    "film-detail": FilmDetail,
    "film-favourite": FilmDetail 
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then( res => res.json())
    .then(films => this.films = films);

    eventBus.$on('film-favourite', (film) => {
      if (this.favouriteFilms.indexOf(film) == -1)
      this.favouriteFilms.push(film)
    })
  },
  methods: {
    removeFromFavourites: function (film) {
      const index = this.favouriteFilms.indexOf(film)
      this.favouriteFilms.splice(index,1);
    }
  }
}
// Park.prototype.remove = function (dinosaur) {
//   const index = this.dinosaurs.indexOf(dinosaur);
//   this.dinosaurs.splice(index, 1);
// }
</script>

<style lang="css" scoped>
#body {
  display: grid;
  grid-template-rows: 80px auto;
  grid-template-columns: auto auto;
};

.favourites {
}
</style>

