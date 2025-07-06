<script setup lang="ts">
  import Header from '@/components/Header.vue'
  import { RouterView } from 'vue-router';
  
  const projectTitle = 'Vue Router Test';
</script>

<template>
  <Header :projectTitle="projectTitle" />

  <section>
        <div class="container">
          <RouterView />
        </div>
  </section>
</template>

<style scoped>
</style>
