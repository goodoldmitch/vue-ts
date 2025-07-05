<script setup lang="ts">

defineProps<{
    pagesNumber: number,
    currentPage: number,
    isLoading: boolean
}>()

const emit = defineEmits<{
    (e: 'switchPage', value: number): void
}>()

function switchPage(pageNumber: number){
    emit('switchPage', pageNumber)
}
</script>

<template>
    <div class="pagination" v-if="!isLoading">
        <button 
            v-for="pageNumber in pagesNumber" 
            :key="pageNumber" 
            id="pageNumber" 
            :disabled="pageNumber === currentPage"
            @click="switchPage(pageNumber)"
        >
            {{ pageNumber }}
        </button>
    </div>
</template>


<style scooped>
    .pagination{
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 5px;
    }
    button{
        width: 30px;
        height: 30px;
        border: none;
        color: #333;
        background: #fff;
        transition: all 300ms ease-in-out;
        cursor: pointer;
    }
    button[disabled], button:hover{
        background: lightblue;
    }
    button[disabled]{
        cursor: auto;
    }
</style>