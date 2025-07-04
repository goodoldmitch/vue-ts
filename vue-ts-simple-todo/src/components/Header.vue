<script setup lang="ts">
    defineProps<{
        usr: string
    }>();
</script>

<template>
    <header>
        <div class="container">
            <h1>ToDo</h1>
            <a href="#" class="user-link">{{ usr }}</a>
        </div>
    </header>
</template>

<style scoped>
    header{
        background: lightblue;
        padding: 20px;
    }
    header .container{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    h1{
        color: #333;
        font-size: 40px;
    }

    .user-link{
        background: lightcoral;
        padding: 10px 20px;
        border-radius: 10px;
        color: #333;
    }
</style>