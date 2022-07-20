<template>
  <div class="pokedex">
    <Search/>
    <Card/>
  </div>
</template>

<script> 

  import Card from '../components/Card.vue'
  import Search from '../components/Search.vue'

  export default {
    name: 'Pokedex',
    components: {
      Card,
      Search
    }
  }

</script>

<style scoped>
  .pokedex{ 
    background-color:  #FFCC00;
    min-height: 100vh; 
  }
</style>
