<template>
  <h1>Caracola Magica</h1>
  <img
    src="https://images.unsplash.com/photo-1580611275653-e2b84d93e2d5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=873&q=80"
    alt="No se puede cargar la imagen"
  />

  <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />
  <p>Tecuerda terminar con un enter la pregunta</p>

  <div>
    <h2>Voy a pasar de año?</h2>
    <h1>SI, NO</h1>
  </div>
</template>

<script>
export default {
  data() {
    pregunta: "Hola Mundo";
  },
};
</script>

<style>
</style>