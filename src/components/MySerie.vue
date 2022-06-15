<template>
  <div class="serie">
    <img :src="'https://image.tmdb.org/t/p/' + 'w154' + serieObject.poster_path" :alt="'immagine ' + serieObject.original_title">
    <span>{{serieObject.original_name}}</span><br>
    <span>{{serieObject.name}}</span><br>
    <span> <LangFlagVue :iso="serieObject.original_language"/> </span><br>
    <span>Voto: {{serieObject.vote_average}}</span><br>
    
  </div>
</template>

<script>


import LangFlagVue from '../../node_modules/vue-lang-code-flags/LangFlag.vue';


export default {
    name: "MySerie",
    props: {
        serieObject: Object
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
