<script setup lang="ts">
  import type { Task } from '@/types/task'
  import { ref } from 'vue'
  import Header from '@/components/Header.vue'
  import TaskForm from '@/components/TaskForm.vue'
  import TaskList from '@/components/TaskList.vue'
  
  const tasksList = ref<Task[]>([]);

  function addNewTask(newTaskAdded: Task){
    tasksList.value.push(newTaskAdded);
    console.log(tasksList);
  }

  function deleteItem(deleteItem: number){
    tasksList.value = tasksList.value.filter((item: Task)=>item.id !== deleteItem);
  }
</script>

<template>
  <Header usr="User Name" />
  <TaskForm @sendNewTask="addNewTask" />
  <TaskList :tasksList="tasksList" @delete-item="deleteItem"/>
</template>

<style scoped>

</style>
