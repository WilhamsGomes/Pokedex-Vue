<template>
    <div>
        <div class="pokemons-cards">
            <div class="card-pok" v-for="pokemon in pokemons.slice(0,150)" :key="pokemon.name">
                <div class="img-card-pokemon">
                    <img 
                    :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${getId(pokemon)}.svg`" 
                    :alt="pokemon.name"/>
                </div>
            
                <h2>{{pokemon.name}}</h2>
                <div class="abilities">
                    <button @click="function () {
                        TogglePopup('buttonTrigger')
                        identificador = getId(pokemon)
                    }">More</button>
                </div>
               
            </div>
        </div>
            
		<Modal :identificador="identificador" v-if="popupTriggers.buttonTrigger" :TogglePopup="() => TogglePopup('buttonTrigger')"/>	
        
    </div>
</template>

<script>

    import axios from 'axios';
    import Modal from './Modal.vue'
    import { ref } from 'vue';

    export default{
        name: 'Card',
        components: {
            Modal
        },

        data(){
            const popupTriggers = ref({
                buttonTrigger: false
            });

            const TogglePopup = (trigger) => {
                popupTriggers.value[trigger] = !popupTriggers.value[trigger]
            }

            return{
                pokemons: [],
			    popupTriggers,
			    TogglePopup,
                identificador: null
            }
        },

        mounted(){
            axios.get("https://pokeapi.co/api/v2/pokemon?limit=151").then((response) => {
                this.pokemons = response.data.results;
            })
        },

        methods: {

            getId(pokemon){
                //this.id = pokemon.url.split("/")[6]
                return pokemon.url.split("/")[6]
            },

            moreInfos(id){
                axios.get("https://pokeapi.co/api/v2/pokemon/"+id).then((response) => {
                    console.log(response.data)
                    console.log("Experiencia: "+response.data.base_experience)
                    console.log("Tipo: "+ response.data.types[0].type.name)
                    console.log("Habilidades: "+response.data.abilities[0].ability.name)
                })
            }

        }
    }

</script>

<style scoped>

.pokemons-cards{
    display: grid;
    grid-template-columns: 300px 300px 300px;
    justify-content: center;
    justify-items: center;
    row-gap: 2em;
    column-gap: 2em;
}

.card-pok{
    display: flex;
    align-items: center;
    flex-direction: column;
    background-color: #F2F2F2;
    height: 400px;
    width: 280px;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
    transition: .5s;
}

.card-pok:hover{
    transform: scale(1.05);
}

img{
    width: 200px;
}

.img-card-pokemon{
    background-color: #C22A22;
    width: 280px;
    height: 300px;
    overflow: hidden;
    margin-bottom: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.card-pok h2{
    text-transform: capitalize;
    text-align:center;
}


.abilities button{
    width: 80px;
    height: 30px;
    border-radius: 15px;
    border: 2px solid #C22A22;
    margin-top: 10px;
}

button:hover{
    cursor: pointer;
}



</style>