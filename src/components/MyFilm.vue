<template>
  <div class="film">
    <img :src="'https://image.tmdb.org/t/p/' + 'w342' + filmObject.poster_path" :alt="'immagine ' + filmObject.original_title">
    
    <div class="description">
      <ul>
        <li>{{filmObject.original_title}}</li><br>
        <li>{{filmObject.title}}</li><br>
        <li> <LangFlagVue :iso="filmObject.original_language"/></li><br>
        <!-- <li>Voto:{{Math.round(filmObject.vote_average / 2)}}</li><br> -->
      </ul>
      <span>
        Voto
        <font-awesome-icon v-for="i in getStarPiene(filmObject.vote_average)" :key="i" icon="fa-solid fa-star" />
      </span><br>
      <span>
        <font-awesome-icon v-for="i in getStarVuote(filmObject.vote_average)" :key="i" icon="fa-regular fa-star" />
      </span>

    </div>
    
  </div>

</template>

<script>


import LangFlagVue from '../../node_modules/vue-lang-code-flags/LangFlag.vue';
import { library } from '@fortawesome/fontawesome-svg-core'
import { faUserSecret } from '@fortawesome/free-solid-svg-icons'

library.add(faUserSecret)

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
    methods:{
      getStarPiene(element){
        let calcPiene = parseInt(Math.round(element/2))
        return calcPiene
         
      },
      getStarVuote(element){
        let calcVuote = parseInt(Math.round(5 - (element/2)));
        return calcVuote;
      }

    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.film{
  display: flex;
}

</style>
