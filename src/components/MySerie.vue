<template>
  <div class="serie">
    
    <div class="container-img">
      <img :src="'https://image.tmdb.org/t/p/' + 'w342' + serieObject.poster_path" :alt="'immagine ' + serieObject.original_title">

    </div>

    <div class="description">
      <ul>
        <li><span>Titolo: </span> {{serieObject.name}}</li>
        <li><span>Titolo Originale: </span>{{serieObject.name}}</li>
        <li><span>Lingua: </span>: <LangFlagVue :iso="serieObject.original_language"/></li>
        <li><span>Overview: </span>{{serieObject.overview}}</li>
        <!-- <li>Voto:{{Math.round(serieObject.vote_average / 2)}}</li><br> -->
      </ul>

      <div class="voto">
        <span>
          Voto
          <font-awesome-icon v-for="i in getStarPiene(serieObject.vote_average)" :key="i" icon="fa-solid fa-star" />
        </span>
        <span>
          <font-awesome-icon v-for="i in getStarVuote(serieObject.vote_average)" :key="i" icon="fa-regular fa-star" />
        </span>

      </div>

    </div>
    
  </div>
</template>

<script>


import LangFlagVue from '../../node_modules/vue-lang-code-flags/LangFlag.vue';
import { library } from '@fortawesome/fontawesome-svg-core'
import { faUserSecret } from '@fortawesome/free-solid-svg-icons'

library.add(faUserSecret)


export default {
  name: "MySerie",
  props: {
    serieObject: Object
  },
  data() {
    return {};
  },

  components: { LangFlagVue },

  methods: {
    getStarPiene(element) {
      let calcPiene = parseInt(Math.round(element / 2))
      return calcPiene

    },
    getStarVuote(element) {
      let calcVuote = parseInt(Math.round(5 - (element / 2)));
      return calcVuote;
    }

  },
}

</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.serie{
  margin-bottom: 50px;
  border: 1px solid white;
  
  // display: flex;

  .container-img{
    position: absolute;
    display: block;
    
    &:hover{
      display: none;
      
    }
  }


  .description{
    width: 341px;
    height: 512px;
    background-color: black;
    color: white;
    padding-top: 40px 10px;

    ul{
      padding: 40px 10px;

     li{
      margin: 5px 0;
      span{
        font-weight: bolder;
      }
     }
    }

    .voto{
      padding-left: 10px;
    }
    
  
  }



}
</style>
