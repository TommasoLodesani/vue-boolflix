<template>
  <div class="film">
    <span>{{filmObject.original_title}}</span><br>
    <span></span><br>
    <span></span><br>
    <span></span>


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
