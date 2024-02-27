<template>
    <form @submit.prevent="submitForm" class="my-form">
      <div class="form-group">
        <label for="name">Nombre:</label>
        <input type="text" id="name" v-model="formData.name" required>
      </div>
  
      <div class="form-group">
        <label for="lastName">Apellido:</label>
        <input type="text" id="lastName" v-model="formData.lastName" required>
      </div>
  
      <div class="form-group">
        <label for="age">Edad:</label>
        <input type="number" id="age" v-model="formData.age" required>
      </div>
  
      <div class="form-group">
        <label for="gender">Género:</label>
        <MySelect v-model="formData.gender" :options="genderOptions" />
      </div>
  
      <div class="form-group">
        <label for="phone">Teléfono:</label>
        <input type="tel" id="phone" v-model="formData.phone" required>
      </div>
  
      <button type="submit">Enviar</button>
    </form>
  </template>
  
  <script>
  import { ref, reactive } from 'vue';
  import MySelect from './MySelect.vue';
  
  export default {
    components: {
      MySelect
    },
    setup() {
      const formData = reactive({
        name: '',
        lastName: '',
        age: '',
        gender: '',
        phone: ''
      });
  
      const genderOptions = ref([
        { value: 'masculino', label: 'Masculino' },
        { value: 'femenino', label: 'Femenino' },
        { value: 'otro', label: 'Otro' }
      ]);
  
      const submitForm = () => {
        console.log('Formulario enviado:', formData);
      };
  
      return {
        formData,
        genderOptions,
        submitForm
      };
    }
  };
  </script>  
  
  <style scoped>
  .my-form {
    max-width: 400px;
    margin: auto;
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
    margin-top: 3px;
    margin-bottom: 10px;
  }
  
  button {
    background-color: #4CAF50;
    color: white;
    padding: 10px 15px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #45a049;
  }
  </style>
  