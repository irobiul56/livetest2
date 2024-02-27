<template>
    <div>
      <form @submit.prevent="handleSubmit">
        <label>
          Name:
          <input type="text" v-model="editedTask.name" />
        </label>
        <label>
          Time:
          <input type="number" v-model.number="editedTask.time" />
        </label>
        <button type="submit">Submit</button>
      </form>
    </div>
  </template>
  
  <script setup>
  import { defineProps, emit, ref } from 'vue';
  
  const props = defineProps({
    task: Object,
  });
  
  const editedTask = ref({ ...props.task });
  
  const handleSubmit = () => {
    emit('submit', editedTask.value);
  };
  </script>
  