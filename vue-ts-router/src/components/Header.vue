<script setup lang="ts">
    import { RouterLink } from 'vue-router';

    defineProps<{
        projectTitle: string
    }>()
</script>

<template>
    <header>
        <div class="title">{{ projectTitle }}</div>
        <nav>
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/about">About</RouterLink>
            <RouterLink to="/contacts">Contacts</RouterLink>
        </nav>
    </header>
</template>

<style scoped>
    header{
        display: flex;
        align-items: center;
        justify-content: space-between;
        color: #333;
        background: lightblue;
        padding: 20px;
    }
    .title{
        font-weight: bold;
        font-size: 24px;
    }

    nav{
        display: flex;
        align-items: center;
        justify-content: flex-end;
        gap: 20px;
    }

    nav a{
        font-size: 18px;
        font-weight: bold;
        padding: 10px;
        text-decoration: none;
        border: 1px #333 solid;
        border-radius: 5px;
        transition: all 300ms ease-in-out;
    }

    nav a:hover, nav a.router-link-active{
        background: lightsalmon;
    }

    nav a.router-link-active{
        pointer-events: none;
    }
</style>