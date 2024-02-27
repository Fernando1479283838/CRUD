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
