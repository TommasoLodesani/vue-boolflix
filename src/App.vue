<template>
  <div id="app">

    <ListFilm/>

     <!-- <font-awesome-icon icon="user-secret" /> -->

  </div>
</template>

<script>

import ListFilm from './components/ListFilm.vue'



export default {
  name: 'App',
  components: {
    ListFilm,

  },
  
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;

  ul{
    list-style-type: none;
  }
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: gray;
  // text-align: center;
  // color: #2c3e50;
  // margin-top: 60px;

  
}
</style>

