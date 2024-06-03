<template>
  <div class="videojuegos-grid">
    <table>
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Plataforma</th>
          <th>Estado</th>
          <th>Puntaje</th>
        </tr>
      </thead>
      <tbody>
        <!-- Acá se completan todos los campos de la grilla con los recibidos en el formulario -->
        <tr v-for="(videojuego, index) in videojuegos" :key="index">
          <td>{{ videojuego.nombre }}</td>
          <td>{{ videojuego.plataforma }}</td>
          <td>{{ videojuego.estado }}</td>
          <td>{{ videojuego.puntaje }}</td>
          <td><button @click="showDetails(videojuego)">Detalles</button></td>
          <td>
            <!-- Acá se cargan todos los datos cuando se hace click sobre el botón "Detalles" -->
            <div v-if="videojuegoSeleccionado === videojuego">
              <h2>Detalles del videojuego</h2>
              <p>Nombre: {{ videojuego.nombre }}</p>
              <p>Plataforma: {{ videojuego.plataforma }}</p>
              <p>Estado: {{ videojuego.estado }}</p>
              <p>Puntaje: {{ videojuego.puntaje }}</p>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

export default {
  props: {
    videojuegos: Array
  },
  data(){
    return {
      videojuegoSeleccionado: null
    }
  },
  methods: {
    showDetails(videojuego) {
      if (this.videojuegoSeleccionado === videojuego) {
        this.videojuegoSeleccionado = null; // Ocultar detalles si ya están mostrados
      } else {
        this.videojuegoSeleccionado = videojuego;
      }
    }
  }
}
</script>



<style scoped>
.videojuegos-grid {
  margin: 20px;
  border-radius: 12px;
}

table {
  width: 100%;
  border-collapse: collapse;
  border-radius: 12px;
}

th,
td {
  padding: 12px;
  background-color: #f8ebff;
  border-bottom: 0.1px solid;
  border-color: #9231a8;
}

th {
  text-align: left;
  background-color: #9231a8;
  color: white;
  border-color: #9231a8;
}

td button {
  padding: 8px 16px;
  background-color: #9231a8;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

td button:hover {
  background-color: #662076;
}

.details {
  background-color: #f9f9f9;
  padding: 16px;
  border-radius: 4px;
  margin-top: 8px;
}

</style>