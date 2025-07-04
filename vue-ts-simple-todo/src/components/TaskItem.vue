<script setup lang="ts">

    const props = defineProps<{
        id: number,
        title: string,
        description: string
    }>();
    
    const emit = defineEmits<{
        (e: 'deleteItem', value: number): void
    }>();

    function deleteItem(){
        emit('deleteItem', props.id);
    }
</script>

<template>
    <div class="task-item">
        <div class="task-item-txt">
            <h3>{{ props.title }}</h3>
            <p>{{ props.description }}</p>
        </div>
        <button class="delete" @click="deleteItem">Delete</button>
    </div>
</template>

<style scoped>
    .task-item{
        display: flex;
        align-items: center;
        justify-content: space-between;
        background: #fff;
        color: #333;
        padding: 20px;
        margin-bottom: 20px;
    }
    .delete{
        background: pink;
        border: none;
        padding: 10px 15px;
        transition: all 300ms ease-in-out;
    }
    .delete:hover{
        opacity: 0.8;
    }
</style>