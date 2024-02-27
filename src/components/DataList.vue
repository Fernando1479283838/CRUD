<template>
  <div class="data-list">
    <h2>{{ message }}</h2>
    <ul>
      <li v-for="(item, index) in dataList" :key="index" :style="{ color: item.textColor, backgroundColor: item.bgColor }">
        {{ item.value }}
      </li>
    </ul>
    <div>
      <label for="newValue">Nuevo Valor:</label>
      <input id="newValue" v-model="newValue" />
      <button @click="addItem">Agregar</button>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  props: {
    dataList: Array,
  },
  setup(props) {
    const message = ref('Lista de Datos Generados');
    const showImage = ref(true);
    const newValue = ref('');

    const toggleImageVisibility = () => {
      showImage.value = !showImage.value;
    };

    const addItem = () => {
      if (isValidValue(newValue.value)) {
        const newItem = {
          id: props.dataList.length + 1,
          value: newValue.value,
          textColor: 'black',
          bgColor: 'white',
        };
        props.dataList.push(newItem);
        newValue.value = '';
      }
    };

    const isValidValue = (value) => {
      return value !== null && value.length > 0;
    };

    return {
      message,
      showImage,
      newValue,
      toggleImageVisibility,
      addItem,
    };
  },
};
</script>

<style scoped>
.data-list {
  background-color: #f0f0f0;
  padding: 20px;
  border-radius: 5px;
  margin-bottom: 20px;
}

button {
  margin-bottom: 10px;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  margin-bottom: 5px;
}

/* Agrega estilos según tus preferencias */
</style>
