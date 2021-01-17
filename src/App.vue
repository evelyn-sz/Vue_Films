<template lang="html">
  <div>
    <h1>Films</h1>
      <div>
        <films-list :films="films"></films-list>
      </div>
  </div>
</template>

<script>

import FilmsList from './components/FilmsList.vue';

export default {
  data() {
    return {
      films: []
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then( res => res.json())
    .then(films => this.films = films);
  },
  components: {
    "films-list": FilmsList
  }
}
</script>

<style lang="css" scoped>

</style>