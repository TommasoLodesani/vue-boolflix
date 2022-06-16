<template>
  <div>

    <header>
      <h2>BOOLFLIX</h2>
      <MySearch @mysearch="searchFilm" />

    </header>

    <main>
      <MyFilm v-for="(film, index) in listaFilm" :key="index" :filmObject="film" />
      <MySerie v-for="(serie, index) in listaSerie" :key="index" :serieObject="serie" />
    </main>


  </div>
</template>

<script>

import axios from "axios";
import MyFilm from "./MyFilm.vue";
import MySerie from "./MySerie.vue";
import MySearch from "./MySearch.vue";

export default {
  name: 'ListFilm',
  components: {
    MyFilm,
    MySearch,
    MySerie

  },
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=961b93e1f77f38aec4ae0478827c4d1f&language=it_IT",
      apiUrlSerie: "https://api.themoviedb.org/3/search/tv?api_key=961b93e1f77f38aec4ae0478827c4d1f&language=it_IT",
      listaFilm: [],
      listaSerie: [],
      userText: "",
      voto:""
    }
  },
  created() {
    this.getFilm();
  },

  methods: {
    // axios
    getFilm() {
      if (this.userText !== "") {

        let currentUrl = this.apiUrl + "&query=" + this.userText;
        // console.log(+ currentUrl);
        // console.log(+ this.userText);

        axios.get(currentUrl)
          .then(result => {
            this.listaFilm = result.data.results
            // console.log(+ this.listaFilm);

          })
          .catch((error) => {
            console.log("errore", error);
          }),

        this.getSerie();
      }
      },

    getSerie() {
      if (this.userText !== "") {

        let currentUrlSerie = this.apiUrlSerie + "&query=" + this.userText;
        // console.log(+ currentUrlSerie);
        // console.log(+ this.userText);

        axios.get(currentUrlSerie)
          .then(result => {
            this.listaSerie = result.data.results
            // console.log(+ this.listaSerie);

          })
          .catch((error) => {
            console.log("errore", error);
          })
      }

    },
    searchFilm(textUser) {
      this.userText = textUser;
      this.getFilm();

    },
  },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

header{
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 40px;
  background-color: black;

  h2{
    color: red;
  }
}
main{
  display: flex;
  }

</style>
