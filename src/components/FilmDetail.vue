<template lang="html">
    <div v-if="film">
        <div id="detailWrapper">
            <h2>{{ film.title }}</h2>
            <div id="flexWrapper">
                <div id="left">
                    <p><span>Director: </span>{{ film.director }}</p>
                    <p><span>Release date: </span>{{ film.release_date }}</p>
                    <p><span>Characters: </span></p>
                        <ul v-for="character in film.people">
                            <li>{{ character }} </li>
                        </ul>

                    <p><span>Species: </span></p>
                        <ul v-for="specie in film.species">
                            <li>{{ specie }} </li>
                        </ul>

                </div>
            </div>
        </div>

    </div>
  
</template>

<script>
export default {
    name: 'film-detail',
    props: ['film']
}
</script>

<style>

</style>