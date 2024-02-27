<<<<<<< HEAD
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
=======
<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import Menu from './components/Menu.vue';
import DataList from './components/DataList.vue';
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
>>>>>>> a68497c1e2c2b4a014d91acbd37d6b590ebd8fca
}
</style>
