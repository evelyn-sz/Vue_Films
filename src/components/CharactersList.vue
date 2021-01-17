<template lang="html">
  <div id="charactersList">
    <ul>
      <list-component v-for="(character, index) in characters" :character="character" :key="index"></list-component>
    </ul>
  </div>
</template>

<script>
import ListComponent from './ListComponent.vue';
export default {
  name: 'characters-list',
  props: ['characters'],
  components: {
    'list-component': ListComponent
  }
}
</script>

<style>

</style>