<<<<<<< HEAD
<!-- Menu.vue -->
<template>
  <div class="menu">
    <button @click="reverseMenuOrder">Revertir Orden</button>
    <ul>
      <template v-for="(item, index) in menu" :key="index">
        <li v-if="isPrime(index)" :key="'prime_' + index">
          <span v-bind:style="{ textDecoration: 'line-through' }">{{ item.value }}</span>
        </li>
        <li v-else :key="'non-prime_' + index">
          <router-link :to="{ name: 'DataDetail', params: { id: item.id } }">{{ item.value }}</router-link>
        </li>
      </template>
    </ul>
  </div>
</template>

<script>
// Importa la función isPrime
import { isPrime } from "@/isPrime";

export default {
  props: {
    menuItems: Array,
  },
  setup(props) {
    const reverseMenuOrder = () => {
      props.menuItems.reverse();
    };

    return {
      isPrime,
      reverseMenuOrder,
    };
  },
};
</script>

<style scoped>
.menu {
  background-color: #f0f0f0;
  padding: 10px;
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

</style>
=======
<template>
    <div class="menu-container">
      <ul>
        <li v-for="(item, index) in menu" :key="index" v-if="!isPrime(index)">
          <router-link :to="item.path">{{ item.label }}</router-link>
        </li>
      </ul>
      <button @click="reverseMenu">Revertir Menú</button>
    </div>
  </template>
  
  <script>
import { MenuItem } from '@/interfaces/MenuInterface';
import { menuData } from '@/data/menuData';
  
  export default {
    data() {
      return {
        menu: menuData,
      };
    },
    methods: {
      isPrime(num) {
        for (let i = 2; i < num; i++) {
          if (num % i === 0) return false;
        }
        return num !== 1;
      },
      reverseMenu() {
        this.menu.reverse();
      },
    },
  };
  </script>
  
  <style scoped>
  .menu-container {
    margin-top: 20px;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    margin: 5px 0;
  }
  
  button {
    margin-top: 10px;
  }
  </style>
  
>>>>>>> a68497c1e2c2b4a014d91acbd37d6b590ebd8fca
