<template>
  <div class="film">
    <img :src="'https://image.tmdb.org/t/p/' + 'w154' + filmObject.poster_path" :alt="'immagine ' + filmObject.original_title">
    <span>{{filmObject.original_title}}</span><br>
    <span>{{filmObject.title}}</span><br>
    <span> <LangFlagVue :iso="filmObject.original_language"/> </span><br>
    <span>Voto: {{filmObject.vote_average}}</span><br>
  </div>

</template>

<script>


import LangFlagVue from '../../node_modules/vue-lang-code-flags/LangFlag.vue';


export default {
    name: "MyFilm",
    props: {
        filmObject: Object
    },
    data() {
        return {};
    },
    components: { LangFlagVue }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
