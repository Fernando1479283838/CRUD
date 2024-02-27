<template>
    <select v-model="selectedOption" required class="my-select">
      <option v-for="option in options" :key="option.value" :value="option.value">
        {{ option.label }}
      </option>
    </select>
  </template>
  
  <script>
  import { ref, defineProps } from 'vue';
  
  export default {
    props: {
      modelValue: String,
      options: Array
    },
    setup(props) {
      const selectedOption = ref(props.modelValue);
  
      return {
        selectedOption
      };
    },
    watch: {
      selectedOption() {
        this.$emit('update:modelValue', this.selectedOption);
      }
    }
  };
  </script>
  
  <style scoped>
  .my-select {
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
    margin-top: 3px;
    margin-bottom: 10px;
  }
  </style>
  