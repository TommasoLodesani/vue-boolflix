<template>
  <div class="film">
    <img :src="'https://image.tmdb.org/t/p/' + 'w342' + filmObject.poster_path" :alt="'immagine ' + filmObject.original_title">
    <span>{{filmObject.original_title}}</span><br>
    <span>{{filmObject.title}}</span><br>
    <span> <LangFlagVue :iso="filmObject.original_language"/></span><br>
    <span>Voto:{{vote_average}}</span><br>
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
        return {
          number: ""
          
        };
    },
    components: { LangFlagVue },
    
    computed: {

      intNumber(){

        return{
         
        }
        
      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
