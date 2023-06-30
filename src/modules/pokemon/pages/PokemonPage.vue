<template>
  <h1>Juego Pokemon</h1>

  <PokemonImg :pokemonId="7" :muestraPokemon="false" />

  <PokemonOps :opciones="arreglo"/>
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
      arreglo:[]
    }
  },
  methods: {
    async cargaJuegoInicial() {
      const arregloPokemons=await obtenerFachadaPokemons();
      this.arreglo=arregloPokemons
      console.log(arregloPokemons)
    },
  },
  mounted() {
    console.log("Se monto el componente");
    this.cargaJuegoInicial();
  },
};
</script>

<style>
</style>