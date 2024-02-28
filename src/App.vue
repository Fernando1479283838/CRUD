<template>
  <div>
    <header class="custom-header">
      <!-- Ruta relativa desde la carpeta src -->
      <img alt="Vue logo" class="logo" src="./logo.png" width="125" height="125" />

      <div class="wrapper">
        <nav class="custom-nav">
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/login">Login</RouterLink>
          <RouterLink to="/registro">Registro</RouterLink>
          <RouterLink to="/tabla-datos">Tabla de Datos</RouterLink>
        </nav>
      </div>
    </header>

    <RouterView class="custom-router-view" />
  </div>
</template>

<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router';
</script>

<style scoped>

.custom-header {
  background-color: #333;
  color: #fff;
  padding: 10px;
  text-align: center;
}

.custom-nav {
  display: flex;
  flex-direction: column; 
  align-items: center;
  margin-top: 10px; 
}

.custom-router-view {
  padding: 20px;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 5px;
}


</style>
