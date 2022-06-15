<template>
  <div class="serie">

    <img :src="'https://image.tmdb.org/t/p/' + 'w342' + serieObject.poster_path"
      :alt="'immagine ' + serieObject.original_title">
    <ul>
      <li>{{ serieObject.original_name }}</li>
      <li>{{ serieObject.name }}</li>
      <li>
        <LangFlagVue :iso="serieObject.original_language" />
      </li>
      <li>Voto:{{Math.round(serieObject.vote_average / 2)}}</li><br>
      <font-awesome-icon v-for="i in getStarPiene(serieObject.vote_average)" :key="i" icon="fa-solid fa-star" />
      <font-awesome-icon v-for="i in getStarVuote(serieObject.vote_average)" :key="i" icon="fa-regular fa-star" />
    </ul>
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
</style>
