<template>
    <div class="nav-bar">
        <div class="logo-pokemon">
            <img src="../assets/img/Pokémon-Logo-PNG.png">
        </div>
        <nav>
            <router-link to="/pokedex">Pokédex</router-link>
            <router-link to="/">Home</router-link>
        </nav>
    </div>
</template>

<script>

export default {
    name: "NavBar"
}

</script>

<style scoped>

.nav-bar{
    /*background-color: #FFCC00;*/
    background-color: #FFCC00;
    color: #000;
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    height: 10vh;
}
.logo-pokemon img{
    width: 150px;
    margin-left: 110px;
}

nav{
    margin-right: 80px;

}

a {
    color: #000;
    font-size: 20px;
    margin: 25px;
    float: right;
    text-align: center;
    font-weight: bold;
    border-bottom: 4px solid #000;
    transition: .3s;
}

a:hover{
    color: #fff;
    border-bottom: 4px solid #fff;
}


</style>