<template>
    <div class="container d-flex align-items-center justify-content-center vh-100">
      <div class="task-list">
        <slot name="header" />
        <ul class="list-group">
          <TaskItem
            v-for="task in tasks"
            :key="task.id"
            :task="task"
            @taskCompleted="handleTaskCompleted"
            @taskDeleted="handleTaskDeleted"
          />
        </ul>
        <div v-if="tasks.length === 0" class="alert alert-info mt-3">No hay tareas en la lista.</div>
        <div class="mt-3">
          <p>Total de tareas: {{ totalTasks }}</p>
          <p>Tareas completadas: {{ completedTasks }}</p>
        </div>
        <div class="input-group mt-3">
          <input v-model="newTaskTitle" class="form-control" placeholder="Nueva tarea" />
          <button @click="addTask" class="btn btn-success">Agregar</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import { ref, computed } from 'vue';
  import TaskItem from './TaskItem.vue';
  
  export default {
    components: {
      TaskItem,
    },
    props: ['tasks'],
    setup(props, { emit }) {
      const newTaskTitle = ref('');
  
      const totalTasks = computed(() => props.tasks.length);
      const completedTasks = computed(() => props.tasks.filter(task => task.completed).length);
  
      const addTask = () => {
        if (newTaskTitle.value.trim() !== '') {
          const newTask = {
            id: Date.now(),
            title: newTaskTitle.value.trim(),
            completed: false,
          };
          emit('taskAdded', newTask);
          newTaskTitle.value = '';
        }
      };
  
      const handleTaskCompleted = (taskId) => {
        emit('taskCompleted', taskId);
      };
  
      const handleTaskDeleted = (taskId) => {
        emit('taskDeleted', taskId);
      };
  
      return {
        newTaskTitle,
        totalTasks,
        completedTasks,
        addTask,
        handleTaskCompleted,
        handleTaskDeleted,
      };
    },
  };
  </script>
  
  <style scoped>
  .task-list {
    max-width: 400px;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  .empty-message {
    margin-top: 10px;
    color: #888;
  }
  
  .task-stats {
    margin-top: 10px;
    font-size: 14px;
    color: #555;
    display: flex;
    justify-content: space-between;
  }
  
  .task-input {
    margin-top: 10px;
    display: flex;
    gap: 10px;
  }
  
  input {
    flex: 1;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  button {
    background-color: #4caf50;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
  }
  </style>
  