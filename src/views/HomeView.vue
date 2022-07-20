<template>
  <div class="home">
    <div class="frase" data-aos="fade-right" data-aos-duration="3000">
      <h3> <span>Find</span> all your favorite <span>Pokemon</span></h3>
      <p>You can know the type of Pokemon, its strengths, disadvantages and abilities</p>
      <button> <router-link to="/pokedex">See pokemons</router-link> </button>
    </div> 
    <div data-aos="fade-left" data-aos-duration="3000">
       <img src="../assets/img/BannerPokemon.png" alt="Pokemon"/>
    </div>
  </div>
  
</template>

<script>
  import AOS from 'aos';
  import 'aos/dist/aos.css';

  export default {
    name: 'HomeView',
    components: {
      
    }
  }

  AOS.init();
</script>

<style scoped>
  
  .home{
    background-color:  #FFCC00;
    height: 90vh;
    display: flex;
    justify-content: space-between;
    overflow: hidden;
  }

  .home img{
    width: 700px;
    margin-right: 120px;
  }

  .frase{
    margin-left: 120px;
  }
  .frase h3{
    width: 600px;
    font-size: 80px;
    margin-top: 50px;
    font-weight: 400;
  }

  span{
    font-weight:bold;
  }

  .frase p{
    margin-top: 60px;
    width: 450px;
    font-size: 25px;
  }

  .frase button{
    margin-top: 60px;
    width: 150px;
    height: 40px;
    background-color: #EF4036;
    color: #fff;
    font-size: 18px;
    border: none;
    box-shadow: #EF4036 0px 2px 4px, rgba(0, 0, 0, 0.2) 0px -3px 0px inset;
    transition: .5s;
  }
  .frase button:hover{
    cursor: pointer;
    background-color: #c22a22;
  }

  a{
    color:#fff;
  }

</style>
 