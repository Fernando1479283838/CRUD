<!-- App.vue -->
<template>
  <div id="app">
    <form @submit.prevent="submitForm" class="form-container">
      <div class="form-group">
        <label for="nombre">Nombre:</label>
        <input type="text" id="nombre" v-model="nombre" maxlength="18" required>
      </div>

      <div class="form-group">
        <label for="apellido">Apellido:</label>
        <input type="text" id="apellido" v-model="apellido" maxlength="18" required>
      </div>

      <div class="form-group">
        <label for="edad">Edad:</label>
        <input type="number" id="edad" v-model="edad" min="0" max="60" required>
      </div>

      <div class="form-group">
        <label for="genero">Género:</label>
        <select id="genero" v-model="genero" required>
          <option value="Hombre">Hombre</option>
          <option value="Mujer">Mujer</option>
          <option value="Otro">Otro</option>
        </select>
      </div>

      <div class="form-group">
        <label for="telefono">Teléfono:</label>
        <input type="tel" id="telefono" v-model="telefono" maxlength="10" required>
      </div>

      <button type="submit" class="submit-btn">Enviar</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: '',
      apellido: '',
      edad: '',
      genero: '',
      telefono: ''
    };
  },
  methods: {
    submitForm() {
      // Aquí puedes realizar acciones adicionales al enviar el formulario
      console.log('Formulario enviado:', this.nombre, this.apellido, this.edad, this.genero, this.telefono);
    }
  }
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh; /* Ajusta la altura de la pantalla completa */
}

.form-container {
  text-align: left;
  border: 2px solid #ccc;
  padding: 20px;
  border-radius: 10px;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input, select {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
}

.submit-btn {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  font-size: 16px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.submit-btn:hover {
  background-color: #45a049;
}
</style>