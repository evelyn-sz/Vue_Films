<template lang="html">
  <div>
    <h1>Films</h1>
      <div>
        <film-filter-form :films="films"/>
        <film-detail/>
      </div>
  </div>
</template>

<script>

import FilmFilterForm from './components/FilmFilterForm.vue';
import FilmDetail from './components/FilmDetail.vue';

export default {
  data() {
    return {
      films: []
    }
  },
  components: {
    "film-filter-form": FilmFilterForm,
    "film-detail": FilmDetail
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then( res => res.json())
    .then(films => this.films = films);
  }
}
</script>

<style lang="css" scoped>

</style>