<template>
  <div class="serie">

    <ul>
      <img :src="'https://image.tmdb.org/t/p/' + 'w342' + serieObject.poster_path" :alt="'immagine ' + serieObject.original_title">
      <li>{{serieObject.original_name}}</li>
      <li>{{serieObject.name}}</li>
      <li><LangFlagVue :iso="serieObject.original_language"/></li>
      <li>Voto: {{serieObject.vote_average}}</li>

    </ul>
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
