<template>
  <h1>Caracola Magica</h1>
  <img v-if="urlImagen" :src="urlImagen" alt="No se puede cargar la imagen" />

  <div class="bg-dark"></div>

  <div class="contenedor">
    <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />
    <p>Recuerda terminar con un signo de pregunta</p>

    <div>
      <h2>{{ pregunta }}</h2>
      <h1>{{ respuesta }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pregunta: "Hola Mundo",
      respuesta: "",
      urlImagen: null,
    };
  },
  watch: {
    pregunta(value, oldValue) {
      console.log(value);
      console.log(oldValue);

      if (value.includes("?")) {
        this.respuesta = "Pensando...";
        this.consumirAPI();
        this.pregunta = "";
      }
    },
  },
  methods: {
    async consumirAPI() {
      const respuesta = await fetch("https://yesno.wtf/api").then((r) =>
        r.json()
      );
      const { answer, image } = respuesta;
      this.respuesta = answer;
      this.urlImagen = image;
    },
  },
};
</script>

<style>
img,
.bg-dark {
  height: 100vh;
  width: 100vw;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
}

.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
}

.contenedor {
  position: relative;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}

p,
h1,
h2 {
  color: white;
}

p {
  font-size: 20px;
  margin-top: 0px;
}
</style>