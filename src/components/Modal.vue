<template>
    <div class="popup">
        <button class="popup-close" @click="TogglePopup()"> X </button>
        <div class="infos-pokemon">
            <div class="informações">
                <div class="info-iniciais-titles">
                    <p>{{namePokemon}} - </p>
                    <p id="value-pokemon">{{identificador}}</p>
                </div>

                <div class="estatisticas">
                    <p class="habilidades" :id="typeBG">Stats: </p>
                    <ul>
                        <li v-for="(estatistica, index) in stats.slice(0,3)" :key="index"> {{estatistica.stat.name}} - {{estatistica.base_stat}}  </li>
                    </ul>
                </div>

                <div class="conteiner-hability">
                    <p class="habilidades" :id="typeBG">Abilities: </p>
                    <ul>
                        <li v-for="(habilidade, index) in abilities" :key="index"> {{habilidade.ability.name}} </li>
                    </ul>
                </div>

                <div class="conteiner-types">
                    <p class="types" :id="typeBG">Types: </p>
                    <ul>
                        <li v-for="(tipo, index) in type" :key="index"> {{tipo.type.name}} </li>
                    </ul>
                </div>

            </div>
            <div class="img-card-pokemon" :id="typeBG">
                <img :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${identificador}.svg`"
                    alt="test" width="200" />
            </div>
        </div>
    </div>
</template>

<script>

import axios from 'axios'

export default {
    name: "Modal",
    props: ['TogglePopup', 'identificador'],

    data() {
        return {
            id_pokemon: null,
            base_experience: null,
            abilities: [],
            type: [],
            typeBG: null,
            namePokemon: null,
            stats: []
        }
    },

    mounted() {
        this.id_pokemon = document.getElementById("value-pokemon").innerHTML;
        this.getInfosPokemon(this.id_pokemon)

    },

    methods: {

        getInfosPokemon(id) {
            axios.get("https://pokeapi.co/api/v2/pokemon/" + id).then((response) => {
                //console.log(response.data)
                this.base_experience = response.data.base_experience
                this.abilities = response.data.abilities
                this.type = response.data.types
                this.typeBG = response.data.types[0].type.name
                this.namePokemon = response.data.name
                this.stats = response.data.stats
                console.log(this.stats)
            })
        }

    }
}
</script>

<style scoped>

.infos-pokemon{
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.popup {
    width: 550px;
    height: 300px;
    position: fixed;
    top: 150px;
    left: 0;
    right: 0;
    bottom: 0;
    margin: 0 auto;
    z-index: 99;
    background-color: #F2F2F2;
    border-radius: 15px;
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
    overflow: hidden;
}
.popup-close {
    position: absolute;
    z-index: 98;
    width: 30px;
    height: 30px;
    border-radius: 50%;
    margin: 5px;
    border: none;
    background-color: #e4e4e4;
}
.popup-close:hover {
    cursor: pointer;
}
.img-card-pokemon{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 350px;
    min-height: 300px;
    border-radius: 15px;
}

.info-iniciais-titles{
    position: absolute;
    display: flex;
    margin: -23px 0px 0px 40px;
    font-size: 20px;
    text-transform: capitalize;
}

.info-iniciais-titles p{
    margin-left: 10px;
}

.estatisticas{
    position: relative;
    margin-top: 10px;
}

ul{
    display: flex;
    flex-wrap: wrap;
    text-transform:capitalize;
}

ul li{
   margin: 5px 10px 5px 10px;
}

.base-expe{
    background-color: #f2f2f2;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    margin: 10px 0px 10px 10px;
    font-size: 20px;
}

.types, .habilidades{
    padding-left: 10px;
    color: #F2F2F2;
    border-radius: 10px;
    min-width: 250px;
}

#steel {
	background-color: #5A8EA2;
}

#fire {
	background-color: #A51900;
}

#grass {
	background-color: #55B036;
}

#electric {
	background-color: #F7E459;
}

#water, #ice {
	background-color: #0F6492;
}

#ground {
	background-color: #D97845;
}

#rock {
	background-color: #B4B3AC;
}

#fairy {
	background-color: #CD8CE2;
}

#poison {
	background-color: #CD56BF;
}

#bug {
	background-color: #91C12F;
}

#dragon {
	background-color: #7C675E;
}

#psychic {
	background-color: #5A36B6;
}

#flying {
	background-color: #A3D2F2;
}

#fighting {
	background-color: #5F8FBD;
}

#normal {
	background-color: #C4BB91;
}


</style>
