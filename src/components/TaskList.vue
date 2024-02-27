 
  <script setup>
  import { ref } from 'vue';
  import TaskForm from './TaskForm.vue';
  
  const tasks = ref([
    { name: 'Task 1', time: 30 },
    { name: 'Task 2', time: 40 },
    { name: 'Task 3', time: 60 },
    { name: 'Task 4', time: 45 },
    { name: 'Task 5', time: 50 },
  ]);
  
  let showForm = ref(false);
  let selectedTask = ref(null);
  
  const editTask = (task) => {
    selectedTask.value = { ...task };
    showForm.value = true;
  };
  
  const updateTask = (updatedTask) => {
    const index = tasks.value.findIndex(task => task.name === updatedTask.name);
    if (index !== -1) {
      tasks.value[index] = { ...updatedTask };
      showForm.value = false;
    }
  };
  </script>

<template>
    <div>
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          {{ task.name }} - {{ task.time }} mins
          <button @click="editTask(task)">Edit</button>
        </li>
      </ul>
      <TaskForm :task="selectedTask" v-if="showForm" @submit="updateTask" />
    </div>
  </template>

  <style scoped>
  </style>
  