<template>
  <div>

    <MySearch @mysearch="searchFilm"/>

    <!-- {{userText}} -->

   
    <MyFilm v-for="(film, index) in listaFilm" :key="index" :filmObject="film" />

  </div>
</template>

<script>

import axios from "axios";
import MyFilm from "./MyFilm.vue";
import MySearch from "./MySearch.vue";

export default {
  name: 'ListFilm',
  components: {
    MyFilm,
    MySearch

  },
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=961b93e1f77f38aec4ae0478827c4d1f&query=" + this.userText,
      listaFilm: [],
      userText: "",
    }
  },
  created() {
    this.getDischi();
  },

  methods: {
    getDischi() {
      axios.get(this.apiUrl)
        .then(result => {
          this.listaFilm = result.data.results
          console.log(this.listaFilm);
          // this.listaFilm = result.data.response

        })

    },
    searchFilm(textUser) {
      this.userText = textUser;
      console.log(this.userSelect);

    },

  },
  computed: {
    filterlistaFilm() {
      // return this.listaDischi;
      return this.listaFilm.filter(item => {
        return item.title.toLowerCase().includes(this.userText.toLowerCase())
      });
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
