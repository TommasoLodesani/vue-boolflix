<template>
  <div class="film">
    
    <div class="container-img">
      <img :src="'https://image.tmdb.org/t/p/' + 'w342' + filmObject.poster_path" :alt="'immagine ' + filmObject.original_title">

    </div>

    <div class="description">
      <ul>
        <li><span>Titolo: </span> {{filmObject.original_title}}</li>
        <li><span>Titolo Originale: </span>{{filmObject.title}}</li>
        <li><span>Lingua: </span>: <LangFlagVue :iso="filmObject.original_language"/></li>
        <li><span>Overview: </span>{{filmObject.overview}}</li>
        <!-- <li>Voto:{{Math.round(filmObject.vote_average / 2)}}</li><br> -->
      </ul>

      <div class="voto">
        <span>
          Voto
          <font-awesome-icon v-for="i in getStarPiene(filmObject.vote_average)" :key="i" icon="fa-solid fa-star" />
        </span>
        <span>
          <font-awesome-icon v-for="i in getStarVuote(filmObject.vote_average)" :key="i" icon="fa-regular fa-star" />
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
