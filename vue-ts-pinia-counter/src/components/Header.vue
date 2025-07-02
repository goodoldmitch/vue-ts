<script setup lang="ts">
    defineProps({
        h1: String
    })
</script>

<template>
    <header>
        <h1>{{ h1 }}</h1>
    </header>
</template>

<style scoped>
    h1{
        font-size: 48px;
        margin-bottom: 40px;
        text-align: center;
    }
</style>