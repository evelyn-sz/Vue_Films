<template lang="html">
  <div>
    <h1>Films</h1>
      <div>
        <film-filter-form :films="films"/>
        <ul>
          <h2 v-on:submit.prevent v-if="favouriteFilms[0]">Favourite films</h2>
            <li v-for="favouriteFilm in favouriteFilms">{{ favouriteFilm.title }}</li>
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
  }
}
</script>

<style lang="css" scoped>

</style>