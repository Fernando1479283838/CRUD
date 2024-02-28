<template>
  <div class="register-container">
    <h2>Registro</h2>
    <form @submit.prevent="registerUser" class="register-form">
      <label for="email">Correo:</label>
      <input type="email" v-model="newUser.email" required>
      <label for="password">Contraseña:</label>
      <input type="password" v-model="newUser.password" required>
      <button type="submit">Registrarse</button>
    </form>
  </div>
</template>

<style scoped>

.register-container {
  max-width: 300px;
  margin: 0 auto;
  background-color: #e0e0e0;
  padding: 20px;
  border: 1px solid #999;
  border-radius: 5px;
}

.register-form {
  display: flex;
  flex-direction: column;
}

.register-form label {
  margin-bottom: 5px;
}

.register-form input {
  padding: 10px;
  margin-bottom: 10px;
}

.register-form button {
  padding: 10px;
  background-color: #28a745;
  color: #fff;
  border: none;
  cursor: pointer;
}

.register-form button:hover {
  background-color: #218838;
}
</style>
