<template>
  <div class="data-table-container">
    <h2>Tabla de Datos</h2>
    <table class="data-table">
      <thead>
        <tr>
          <th>Correo</th>
          <th>Contraseña</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(user, index) in users" :key="index">
          <td>{{ user.email }}</td>
          <td>{{ user.password }}</td>
          <td>
            <button @click="editUser(user)" class="edit-button">Editar</button>
            <button @click="deleteUser(index)" class="delete-button">Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>

    <div v-if="isEditing" class="edit-dialog">
      <h3>Editar Usuario</h3>
      <form @submit.prevent="saveEdit">
        <label for="edit-email" class="edit-label">Correo:</label>
        <input type="email" v-model="editedUser.email" id="edit-email" required>
        <label for="edit-password" class="edit-label">Contraseña:</label>
        <input type="password" v-model="editedUser.password" id="edit-password" required>
        <button type="submit">Guardar</button>
      </form>
      <button @click="cancelEdit">Cancelar</button>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const users = ref([
  { email: 'usuario1@example.com', password: 'password123' },
  { email: 'usuario2@example.com', password: 'password456' },
  // Agrega más datos según sea necesario
]);

const editedUser = ref({ email: '', password: '' });
let editedIndex = -1;
const isEditing = ref(false);

const editUser = (user: any) => {
  editedUser.value = { ...user };
  editedIndex = users.value.indexOf(user);
  isEditing.value = true;
};

const saveEdit = () => {
  users.value.splice(editedIndex, 1, { ...editedUser.value });
  isEditing.value = false;
};

const cancelEdit = () => {
  isEditing.value = false;
};

const deleteUser = (index: number) => {
  users.value.splice(index, 1);
};
</script>

<style scoped>
/* Estilos específicos para la vista de TablaDatos */

.data-table-container {
  max-width: 800px;
  margin: 0 auto;
  background-color: #ffffff;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.data-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

.data-table th,
.data-table td {
  border: 1px solid #dee2e6;
  padding: 0.75rem;
  text-align: left;
}

.data-table th {
  background-color: #007bff;
  color: #fff;
}

.data-table td {
  background-color: #f8f9fa;
  color: #212529;
}

.edit-dialog {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.edit-dialog h3 {
  margin-top: 0;
  color: #333;
}

.edit-dialog .edit-label {
  color: #333;
  display: block;
  margin-bottom: 10px;
}

.edit-dialog input {
  padding: 10px;
  margin-bottom: 10px;
}

.edit-dialog button {
  padding: 10px;
  background-color: #007bff;
  color: #fff;
  border: none;
  cursor: pointer;
}

.edit-dialog button:hover {
  background-color: #0056b3;
}
</style>
