<template>
    <div class="videojuego-form">
      <h2>Agregar videojuego</h2>
      <form @submit.prevent="agregarVideojuego">
        <div class="form-group">
            <label for="nombre">Nombre:</label>
            <input type="text" id="nombre" v-model="nombre" required placeholder="Ingresá el nombre">
        </div>
        <div class="form-group">
          <label for="plataforma">Plataforma:</label>
          <select id="plataforma" v-model="plataforma" required>
            <option value="" disabled selected>-- Seleccioná una plataforma --</option>
            <option value="pc">Pc</option>
            <option value="playstation">Play Station</option>
            <option value="xbox">Xbox</option>
          </select>
        </div>
        <div class="form-group">
          <label for="estado">Estado:</label>
          <select id="estado" v-model="estado" required>
            <option value="" disabled selected>-- Seleccioná un estado --</option>
            <option value="jugando">Jugando</option>
            <option value="terminado">Terminado</option>
            <option value="pendiente">Pendiente</option>
          </select>
        </div>
        <div class="form-group">
          <label for="puntaje">Puntaje:</label>
          <input type="number" id="puntaje" v-model="puntaje" required min="1" max="10" placeholder="Ingresá un puntaje entre 1 y 10">
        </div>
        <button type="submit">Agregar</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        nombre: '',
        plataforma: '',
        estado: '',
        puntaje: ''
      }
    },
    methods: {
      agregarVideojuego() {
        this.$emit('videojuegoAgregado', {
          nombre: this.nombre,
          plataforma: this.plataforma,
          estado: this.estado,
          puntaje: this.puntaje
        })
        this.limpiarFormulario()
      },
      limpiarFormulario() {
        this.nombre = ''
        this.plataforma = ''
        this.estado = 'jugando'
        this.puntaje = 0
      }
    }
  }
  </script>
  
  <style scoped>
  .videojuego-form {
    margin: 20px;
    background-color: #f8ebff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
    color: #333;
  }
  
  input,
  select {
    text-align: center;
    width: calc(100% - 12px);
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 16px;
  }
  
  select {
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    background-color: #fff;
    background-repeat: no-repeat;
    background-position: right 10px center;
  }
  
  button {
    padding: 12px 24px;
    background-color: #9231a8;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #662076;
  }
</style>