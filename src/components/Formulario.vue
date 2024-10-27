<template>
  <section class="container">
    <div class="form">
      <label>Color de fondo</label>
      <input v-model="bgColor" type="text" />

      <label>Color de texto</label>
      <input v-model="textColor" type="text" />

      <div class="checkbox">
        <label>Mostrar texto</label>
        <input type="checkbox" v-model="showText" />
      </div>

      <label>Borde</label>
      <input v-model="border" type="range" min="0" max="100" />

      <label>Contenido textual</label>
      <textarea v-model="content"></textarea>

      <label>Tipografía</label>
      <select v-model="tipografy">
        <option disabled value="">Selecciona una fuente</option>
        <option v-for="font in fonts" :key="font" :value="font">{{ font }}</option>
      </select>

      <div class="checkbox">
        <label>Opaco</label>
        <input type="checkbox" v-model="opacity" />
      </div>

      <label>Tamaño de letra</label>
      <div class="inputRadio">
        <input v-model="fontSize" type="radio" value="pequeño" />Pequeño
        <input v-model="fontSize" type="radio" value="mediano" />Mediano
        <input v-model="fontSize" type="radio" value="grande" />Grande
      </div>
    </div>

    <div
      v-if="showText && content"
      class="figure"
      :class="fontSize"
      :style="{
        backgroundColor: bgColor,
        color: textColor,
        borderRadius: `${border}px`,
        opacity: opacity ? 0.5 : 1,
        fontFamily: tipografy,
      }"
    >
      <p v-show="showText">{{ content }}</p>
    </div>
  </section>
</template>

<script>
export default {
  name: "Formulario",
  data() {
    return {
      bgColor: "",
      textColor: "",
      showText: true,
      border: 0,
      content: "",
      tipografy: "",
      opacity: true,
      fontSize: "mediano",
      fonts: ["Arial", "Verdana", "Tahoma"],
    };
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  gap: 20px;
}

.form {
  display: flex;
  flex-direction: column;
  height: 410px;
  width: 250px;
  padding: 20px;
  border: 1px solid #000;
  background-color: #16423c;
  color: #fff;
  gap: 10px;
}

.checkbox {
  display: flex;
  gap: 8px;
  align-items: center;
}

.figure {
  width: 200px;
  height: 200px;
  border: 2px solid #000;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  transition: opacity 0.3s;
}

.pequeño {
  font-size: 15px;
}

.mediano {
  font-size: 25px;
}

.grande {
  font-size: 35px;
}

.opaque {
  opacity: 0.5;
}
</style>
