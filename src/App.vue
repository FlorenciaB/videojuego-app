<template>
  <div class="app">
    <h1>Mis videojuegos</h1>
    <videojuego-form @videojuego-agregado="agregarVideojuego" />
    <videojuegos-grid :videojuegos="videojuegos" @videojuego-seleccionado="seleccionarVideojuego" />
  </div>
</template>

<script>
//Importación de componentes
import VideojuegoForm from './components/VideojuegoForm.vue';
import VideojuegosGrid from './components/VideojuegosGrid.vue';

export default {
  components: {
    VideojuegoForm,
    VideojuegosGrid
  },
  data() {
  return {
    //Juegos pre cargados
    videojuegos: [
      { nombre: "Videojuego 1", plataforma: "PS5", estado: "Jugando", puntaje: 9 },
      { nombre: "Videojuego 2", plataforma: "PC", estado: "Terminado", puntaje: 8 },
    ],
    videojuegoSeleccionado: null
    }
  },

  //incorporación de métodos
  methods: {
    agregarVideojuego(nuevoVideojuego) {
      this.videojuegos.push(nuevoVideojuego);
    },
    seleccionarVideojuego(videojuego) {
      this.videojuegoSeleccionado = videojuego;
    }
  }
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #575756;
  margin-top: 60px;
}
h1{
  color: #9231a8;
}
</style>
