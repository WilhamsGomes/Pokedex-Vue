<template>
    <div class="search-pok">
        <h3>+500 <span>Pokemons</span> or you to choose your favorite</h3>
    </div>
</template>

<script>
   
    export default{
        name: 'Search'
    }

</script>

<style scoped>

.search-pok{
    display:flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    margin: 50px 0px 50px 0px;
}

.search-pok h3{
    width: 1100px;
    text-align:center;
    font-size: 60px;
    font-weight: 400;
}

.search-pok span{
    font-weight: bold;
}

</style>
