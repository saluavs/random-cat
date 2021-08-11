<template>
  <div id="app">
    <section class="light-blue py-5">
      <h1 class="titulo font-weight-bold">{{ msg }}</h1>
    </section>

    <section class="pink">
      <form class="pt-3">
        <div class="form-group">
          <label>Título:</label>
          <input type="text" class="form-control" v-model="titulo" />
        </div>
        <div class="form-group">
          <label for="">Filtro:</label>
          <select class="form-control" v-model="filtro">
            <option value="blur">Blur</option>
            <option value="mono">Mono</option>
            <option value="sepia">Sepia</option>
            <option value="negative">Negative</option>
            <option value="paint">Paint</option>
            <option value="pixel">Pixel</option>
          </select>
        </div>
        <div class="p-2">
          <label for="">Color:</label>
          <select class="py-1" v-model="color">
            <option value="red">Rojo</option>
            <option value="blue">Azul</option>
            <option value="green">Verde</option>
            <option value="orange">Naranjo</option>
            <option value="white">Blanco</option>
            <option value="yellow">Amarillo</option>
          </select>
          <div class="circle mx-3 py-2" :style="{background: this.color}"></div>
        </div>
        <div class="form-group">
          <label>Tamaño:</label>
          <input 
            type="number"
            v-model="tamano"
            @keyup.enter="mostrarImg"
            placeholder="200,300,400,etc"
          />
        </div>
        <button type="button" class="btn btn-success" @click="mostrarImg">
          Obtener mi gatito
        </button>
      </form>
    </section>

    <section class="light-blue py-5" id="image">
      <div class="mb-5">
        <img :src="urlImage" alt="" />
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      msg: "Random Gif Cat",
      urlImage: null,
      titulo: null,
      color: null,
      filtro: null,
      tamano: null,
    };
  },
  methods: {
    mostrarImg() {
      this.urlImage = `https://cataas.com/cat/gif/says/${this.titulo}?filter=${this.filtro}&color=${this.color}&size=${this.tamano}`;
      console.log("url", this.urlImage);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
.light-blue {
  background-color: lightblue;
}
.circle{
  border-radius: 50%;
  height: 30px;
  width: 30px;
  display: inline-block;
  vertical-align: middle;
}
.pink {
  background-color: #faa7b5;
}
body {
  width: 600px;
  margin: 0 auto;
  padding: 20px 20px 20px 20px;
}
.titulo{
  height: 60px;
  padding-top: 50px;
  margin: 0 auto;
}
</style>
