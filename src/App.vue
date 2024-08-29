<script>
export default {
  name: "App",
  data() {
    return {
      nuevaTarea: "",
      tareas: [],
      nuevoCirculo: "",
      circulos: [],
      fontSize: 20,
      ImgSize: 100,
    };
  },
  methods: {
    saludar() {
      console.log("Hola mi nombre es Diego!");
    },
    despedir() {
      alert("Adios, vuelva pronto!");
    },
    agregarTarea() {
      const nuevaTarea = this.nuevaTarea;
      this.tareas.push(nuevaTarea);
      this.nuevaTarea = "";
    },
    agregarCirculo() {
      const nuevoCirculo = this.nuevoCirculo;
      this.circulos.push(this.nuevoCirculo);
      this.nuevoCirculo = "";
    },

    send() {
      console.log("Enviado");
    },
    incrementar() {
      this.fontSize++;
    },

    disminuir() {
      this.fontSize--;
    },

    incrementarImg() {
      this.ImgSize++;
    },
    disminuirImg() {
      this.ImgSize--;
    },
  },
};
</script>

<template>
  <div>
    <h1 @click="despedir()">1.-Adios!</h1>
    <img
      width="200"
      @dblclick="saludar()"
      src="https://vuejs.org/images/logo.png"
    />

    <h1>2.-TODO</h1>
    <input type="text" v-model="nuevaTarea" />
    <button @click="agregarTarea()">Agregar</button>
    <ul>
      <li v-for="tarea in tareas">
        {{ tarea }}
      </li>
    </ul>

    <h1>3.- Agregar circulos de colores</h1>
    <input type="text" v-model="nuevoCirculo" placeholder="color ej: red" />
    <button @click="agregarCirculo()">agregar</button>
    <ul>
      <li
        v-for="circulo in circulos"
        :style="{ backgroundColor: circulo }"
        class="circuloEstilo"
        :key="circulo"
      ></li>
    </ul>
  </div>

  <h2>4.- Prevent</h2>
  <form @submit.prevent="send">
    <button>Enviar</button>
  </form>

  <h2>5.- Modificador de tecla</h2>
  <input
    :style="{ fontSize: `${fontSize}px` }"
    type="text"
    @keyup.up="incrementar"
    @keyup.down="disminuir"
  />

  <h2>6.- Modificador de tecla para incrementar y disminuir una imagen</h2>
  <input type="text" @keyup.up="incrementarImg" @keyup.down="disminuirImg" />
  <div>
    <img
      src="https://vuejs.org/images/logo.png"
      :width="ImgSize"
      :height="ImgSize"
    />
  </div>
</template>

<style scoped>
.circuloEstilo {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  box-shadow: 2px 2px 2px 2px #ccc;
}
li {
  margin-bottom: 10px;
}
</style>
