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
      apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=961b93e1f77f38aec4ae0478827c4d1f",
      listaFilm: [],
      userText: "",
    }
  },
  created() {
    this.getDischi();
  },

  methods: {
    // axios
    getDischi() {
      if(this.userText !== ""){

        let currentUrl = this.apiUrl + "&query=" + this.userText;
        console.log("questo è il current" + currentUrl);
        console.log(this.userText);

        axios.get(currentUrl)
          .then(result => {
            this.listaFilm = result.data.results
            console.log(this.listaFilm);
            
          })
          .catch((error) => {
            console.log("errore", error);
          })
      }

    },
    searchFilm(textUser) {
      this.userText = textUser;
      console.log(this.userSelect);
      this.getDischi();
      

    },

  },
  computed: {
    // filterlistaFilm() {
    //   // return this.listaDischi;
    //   return this.listaFilm.filter(item => {
    //     return item.title.toLowerCase().includes(this.userText.toLowerCase())
    //   });
    // }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
