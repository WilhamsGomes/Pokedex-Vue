<template>
  <NavBar/>
  <router-view/>
</template>

<script>
    import NavBar from "./components/Navbar.vue"

    export default {
      name: "app",
      components:{
        NavBar
      }
  }

</script>

<style>

  @import url('https://fonts.googleapis.com/css2?family=Anek+Malayalam:wght@500&display=swap');

  body{
    background-color:  #FFCC00;
  }

  * {
    font-family: 'Anek Malayalam';
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  a{
    text-decoration: none
  }

  ul, ol, li {
    list-style: none;
  }

</style>
