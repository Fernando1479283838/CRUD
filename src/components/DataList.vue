<template>
<<<<<<< HEAD
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
=======
    <div class="data-list-container">
      <ul>
        <li v-for="(item, index) in dataList" :key="index">
          <div>
            <span :style="{ color: item.textColor, background: item.bgColor }">{{ item.value }}</span>
            <button @click="changeColor(index)">Cambiar Color</button>
          </div>
        </li>
      </ul>
      <input v-model="newValue" @input="validateAndAdd" placeholder="Nuevo Valor" />
    </div>
  </template>
  
  <script>
  import { DataItem } from '@/interfaces/DataItemInterface';
  import { dataListData } from '@/data/dataListData';
  
  export default {
    data() {
      return {
        dataList: dataListData,
        newValue: '',
      };
    },
    methods: {
      validateAndAdd() {
        if (this.validateInput()) {
          const newItem = { value: this.newValue, textColor: 'black', bgColor: 'white' };
          if (!this.dataList.some(item => item.value === this.newValue)) {
            this.dataList.push(newItem);
            this.newValue = '';
          } else {
            alert('El valor ya existe en la lista.');
          }
        }
      },
      validateInput() {
        return this.newValue.trim().length > 0;
      },
      changeColor(index) {
        const textColor = prompt('Ingrese color de texto:');
        const bgColor = prompt('Ingrese color de fondo:');
        if (textColor && bgColor) {
          this.$set(this.dataList, index, { ...this.dataList[index], textColor, bgColor });
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .data-list-container {
    margin-top: 20px;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    margin: 5px 0;
  }
  
  span {
    padding: 5px;
    margin-right: 10px;
    border: 1px solid #ccc;
  }
  
  button {
    cursor: pointer;
  }
  </style>
  
>>>>>>> a68497c1e2c2b4a014d91acbd37d6b590ebd8fca
