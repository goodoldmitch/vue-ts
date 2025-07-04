<script setup lang="ts">
import type { Task } from '@/types/task'
import TaskItem from '@/components/TaskItem.vue'

defineProps<{
  tasksList: Task[]
}>()

const emit = defineEmits<{
    (e: 'deleteItem', value: number): void
}>();

function deleteItem(deleteItem: number){
    emit('deleteItem', deleteItem);
}
</script>

<template>
  <section class="task-list">
    <div class="container">
      <div class="tasks-list" v-if="tasksList.length > 0">
        <h2>Tasks to do</h2>
        <task-item 
            v-for="task in tasksList"
            :id="task.id" 
            :title="task.title" 
            :description="task.description"
            @delete-item="deleteItem"
            >
        </task-item>
      </div>

      <h2 v-else>Nothing to do</h2>
    </div>
  </section>
</template>

<style scoped>
.task-list {
  padding: 40px 0;
  margin: 40px 0;
}
h2 {
  text-align: center;
  color: #fff;
  font-size: 30px;
  margin-bottom: 30px;
}
</style>
