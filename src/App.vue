<template>
  <div>
    <TaskList :tasks="tasks" @taskAdded="addTask" @taskCompleted="completeTask" @taskDeleted="deleteTask">
      <template v-slot:header>
        <h2>Lista de Tareas</h2>
      </template>
    </TaskList>
  </div>
</template>

<script>
import { ref } from 'vue';
import TaskList from './components/TaskList/TaskList.vue';

export default {
  components: {
    TaskList,
  },
  setup() {
    const tasks = ref([
      { id: 1, title: 'Tarea 1', completed: false },
      { id: 2, title: 'Tarea 2', completed: true },
    ]);

    const addTask = (newTask) => {
      tasks.value.push(newTask);
    };

    const completeTask = (taskId, emit) => {
      console.log('completeTask called with taskId:', taskId);
      const taskIndex = tasks.value.findIndex(task => task.id === taskId);
      if (taskIndex !== -1) {
        tasks.value[taskIndex].completed = !tasks.value[taskIndex].completed;
      }
      emit('taskCompleted', taskId);
    };

    const deleteTask = (taskId) => {
      tasks.value = tasks.value.filter(task => task.id !== taskId);
    };

    return {
      tasks,
      addTask,
      completeTask,
      deleteTask,
    };
  },
};
</script>

