<template>
  <div>

   
    <MyFilm v-for="(film, index) in listaFilm" :key="index" :filmObject="film" />

  </div>
</template>

<script>

import axios from "axios";
import MyFilm from "./MyFilm.vue";
// import MySelect from "./MySelect.vue";

export default {
  name: 'ListFilm',
  components: {
    MyFilm,

  },
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=961b93e1f77f38aec4ae0478827c4d1f&language=it-IT&page=1&include_adult=false&query=ritorno+al+futuro",
      listaFilm: [],
      userSelect: "",
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
    searchGenre(selectUser) {
      this.userSelect = selectUser;
      console.log(this.userSelect);

    },

  },
  computed: {
    filterListaDischi() {
      // return this.listaDischi;

      return this.listaDischi.filter(item => {
        return item.genre.includes(this.userSelect)
      });
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
