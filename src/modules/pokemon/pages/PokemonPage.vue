<template>
<h1 v-if="!pokemonCorrecto">Espere por favor....</h1>

<div v-else>
  <h1>Juego Pokemon</h1>

  <PokemonImg  :pokemonId="pokemonCorrecto.id" :muestraPokemon="showPokemon" />

  <PokemonOps :opciones="pokemonArr" @seleccionado="revisarSeleccion($event)" />
  </div>
</template>

<script>
import PokemonImg from "../components/PokemonImg.vue";
import PokemonOps from "../components/PokemonOps.vue";

import obtenerFachadaPokemons from "../helpers/clientePokemonAPI";

console.log();
export default {
  components: {
    PokemonImg,
    PokemonOps,
  },
  data(){
    return{
      pokemonArr:[],
      pokemonCorrecto: null,
      showPokemon: false
    }
  },
  methods: {
    async cargaJuegoInicial() {
      const arregloPokemons=await obtenerFachadaPokemons();
      this.pokemonArr=arregloPokemons
      console.log(arregloPokemons)
      const indicePokemon = Math.floor(Math.random()*4)
      this.pokemonCorrecto = this.pokemonArr[indicePokemon]
    },
    revisarSeleccion(idSeleccionado){
      console.log("Evento del padre")
      console.log(idSeleccionado)

      if(idSeleccionado==this.pokemonCorrecto.id){
        this.showPokemon=true
        console.log("Felicitaciones")
      }else{
        this.showPokemon=false
        console.log("Error")
      }
    }
  },
  mounted() {
    console.log("Se monto el componente");
    this.cargaJuegoInicial();
  },
};
</script>

<style>
</style>