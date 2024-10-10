<template>
  <div class="container">
    <div id="control-panel">
      <label>Color de fondo</label>
      <input type="text" v-model="bgColor" />

      <label>Color de texto</label>
      <input type="text" v-model="textColor" />

      <div class="input-cbox">
        <input type="checkbox" v-model="showText" /> Mostrar texto
      </div>

      <label>Borde</label>
      <input type="range" v-model="customBorder" min="0" max="100" />

      <label>Contenido textual</label>
      <textarea v-model="text" cols="30" rows="5"></textarea>

      <label>Tipografia</label>
      <select v-model="selectedTypography">
        <option disabled value="">Seleccione un color</option>
        <option v-for="typo in typography" :value="typo">{{ typo }}</option>
      </select>

      <div class="input-cbox">
        <input type="checkbox" v-model="opacity" /> Opaco
      </div>

      <label>Tamaño de letra</label>
      <div class="input-radio">
        <input type="radio" v-model="fontSize" value="fontSmall" /> 16px
        <input type="radio" v-model="fontSize" value="fontMedium" /> 24px
        <input type="radio" v-model="fontSize" value="fontLarge" /> 32px
      </div>
    </div>

    <div
      id="preview-box"
      :style="{
        backgroundColor: bgColor,
        color: textColor,
        borderRadius: `${customBorder}px`,
        fontFamily: selectedTypography,
        opacity: opacity ? 0.5 : 1,
      }"
      :class="fontSize"
    >
      <p v-show="showText">
        {{ text }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CustomBox",
  data() {
    return {
      bgColor: "",
      textColor: "",
      showText: true,
      customBorder: 0,
      text: "",
      typography: ["cursive", "monospace", "serif", "sans-serif"],
      selectedTypography: "",
      opacity: false,
      fontSize: "fontMedium",
    };
  },
};
</script>

<style>
#control-panel {
  display: flex;
  flex-direction: column;
  width: 400px;
  height: max-content;
  background-color: #0f675d;
  color: white;
  padding: 20px;
}
#preview-box {
  width: 400px;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  margin: auto;
}
input,
textarea,
select {
  margin-bottom: 20px;
  resize: none;
}
.container {
  margin: auto;
  display: flex;
  justify-content: space-evenly;
}

.fontSmall {
  font-size: 16px;
}
.fontMedium {
  font-size: 24px;
}
.fontLarge {
  font-size: 32px;
}
</style>
