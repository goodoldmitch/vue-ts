<script setup lang="ts">
    import type { Task } from '@/types/task'
    import { ref } from 'vue'
    const inputTitle = ref(''),
          inputDescription = ref('');

    const emit = defineEmits<{
        (e: 'sendNewTask' , value: Task): void
    }>();
    
    function addTask(){

        const newTaskAdded: Task = {
            id: Date.now(),
            title: inputTitle.value,
            description: inputDescription.value
        }
        if(!inputTitle.value || !inputDescription.value){
            alert('all fields are required');
        }else{ 
            emit('sendNewTask', newTaskAdded);

            inputTitle.value = '';
            inputDescription.value = '';
        }
    }
</script>

<template>
    <section class="form">
        <h2>Add task</h2>
        <div class="container">
            <form class="task-add-form" @submit.prevent="addTask">
                <input type="text" v-model="inputTitle" name="title">
                <input type="text" v-model="inputDescription">
                <button class="add-button">Add task</button>
            </form>
        </div>
    </section>
</template>

<style scoped>
    .form{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 20px;
        width: 100%;
        padding: 40px 0 0;
    }
    h2{
        font-size: 30px;
    }
    .form .container{
        width: 100%;
    }
    .task-add-form{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 20px;
    }
    .task-add-form input{
        width: 100%;
        padding: 10px 15px;
        box-shadow: inset 0 0 5px rgba(0,0,0,.5);
    }
    .add-button{
        align-self: flex-end;
        border: none;
        background: lightblue;
        padding: 10px 15px;
        transition: all 300ms ease-in-out;
    }
    .add-button:hover{
        opacity: 0.8;
    }
</style>