<script setup lang="ts">
 defineProps<{mainHeader : string}>();
</script>

<template>
    <header>
        <h1>{{ mainHeader }}</h1>    
    </header>
</template>

<style scoped>
    header{
        padding: 10px;
        background: lightblue;
    }
    h1{
        text-align: center;
    }
</style>
