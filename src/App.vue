<template lang="html">
  <div>
    <h1>Species</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      species: []
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/species')
    .then( res => res.json())
    .then(species => this.species = species);
  }
}
</script>

<style>

</style>