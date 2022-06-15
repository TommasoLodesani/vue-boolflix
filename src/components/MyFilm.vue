<template>
  <div class="film">
    <span>{{filmObject.original_title}}</span><br>
    <span>{{filmObject.title}}</span><br>
    <span>{{filmObject.original_language}}</span><br>
    <span>{{filmObject.vote_average}}</span><br>
    


  </div>
</template>

<script>



export default {
  name: 'MyFilm',
  props : {
    filmObject : Object
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
