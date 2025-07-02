<script setup lang="ts">
  import { useCounterStore } from '../stores/counter'

  const store = useCounterStore();
  
</script>

<template>
  <p>{{ store.count  }} - this value is taken from Pinia store</p>
</template>

<style scoped>
  p{
    font-size: 18px;
    margin-top: 20px;
    text-align: center;
  }
</style>
