<template>
  <div id="app">
    <Menu :menuItems="menuItems" />
    <DataList :dataList="dataList" />
  </div>
</template>

<script>
import Menu from '@/components/Menu.vue';
import DataList from '@/components/DataList.vue';
import { ref } from 'vue';

export default {
  components: {
    Menu,
    DataList,
  },
  setup() {
    const menuItems = ref(['Home', 'Profile', 'About', 'Contact']);

    const dataList = ref([
      { id: 1, value: 'Rojo', textColor: 'black', bgColor: 'white' },
      { id: 2, value: 'Azul', textColor: 'black', bgColor: 'white' },
      { id: 3, value: 'Verde', textColor: 'black', bgColor: 'white' },
    ]);

    const reverseMenuOrder = () => {
      menuItems.value.reverse();
    };

    const addItem = (newValue) => {
      if (isValidValue(newValue)) {
        const newItem = {
          id: dataList.value.length + 1,
          value: newValue,
          textColor: 'black',
          bgColor: 'white',
        };
        dataList.value.push(newItem);
      }
    };

    const isValidValue = (value) => {
      return value !== null && value.length > 0;
    };

    return {
      menuItems,
      dataList,
      reverseMenuOrder,
      addItem,
    };
  },
};
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}
</style>
