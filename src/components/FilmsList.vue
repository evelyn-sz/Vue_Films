<template lang="html">
    <div>
        <ul>
            <li>
                <list-component v-for="film in films"></list-component>
            </li>
        </ul>
    </div>
  
</template>

<script>

import ListComponent from './ListComponent.vue';
export default {
    name: 'films-list',
    props: ['films'],
    components: {
        "list-component": ListComponent
    }
}
</script>

<style lang="css" scoped>

</style>