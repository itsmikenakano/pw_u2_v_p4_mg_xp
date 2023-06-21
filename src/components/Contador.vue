<template>
  <h3>{{ evaluarTitulo}}</h3>
  <p>{{ numero }}<sup>2 </sup>={{ obtenerCuadradoComputado }}</p>
  <p>{{ numero }}<sup>2 </sup>={{ obtenerCuadradoComputado }}</p>
  <p>{{ numero }}<sup>2 </sup>={{ obtenerCuadradoComputado }}</p>
  <button @:click="incrementar()">+</button>
  <button v-on:click="decrementar()">-</button>
</template>

<script>
export default {
  //dar un nombre especifico al componente, no siempre va a ser igual al del arvhibo
  name: "Contador",
  data() {
    return {
      numero: this.inicio,
      tituloComponente: this.titulo,
    };
  },
  methods: {
    obtenerCuadrado() {
      console.log("Entro al metodo cuadrado");
      return this.numero * this.numero;
    },

    incrementar() {
      this.numero += 1;
    },

    decrementar() {
      this.numero -= 1;
    },
  },

  computed: {
    obtenerCuadradoComputado() {
      console.log("Entro al metodo cuadrado computado");
      return this.numero * this.numero;
    },
    evaluarTitulo(){
      return this.tituloComponente ||'Valor por defecto';
    }
  },
  props: {
    titulo: String,
    inicio: {
      type:Number,
      required: false,
      default: 100,
      validator(value) {
          return value > 100
      }
    }
  }
};
</script>

<style>
button {
  background-color: #64b687;
  border-radius: 5px;
  border: 1px solid white;
  color: white;
  cursor: pointer;
  margin: 0 5px;
  padding: 5px 15px;
}

button:hover {
  background-color: #03c457;
}
</style>