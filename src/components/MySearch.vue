<template>
  <div>

    <input type="text" v-model="inputText"
    @keyup.enter="$emit('mysearch',inputText )">
   
  </div>
</template>

<script>



export default {
  name: 'MySearch',
  data(){
    return{
        inputText: "",
        
    }
  }, 
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
