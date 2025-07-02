<script setup lang="ts">
  import { useCounterStore } from '../stores/counter'

  const store = useCounterStore();
  
</script>

<template>
  <div class="count-number"> {{ store.count }}</div>
  <div class="buttons-block">
    <button @click="store.decrement()" class="decrement">decrement</button>
    <button @click="store.reset()" class="reset">reset</button>
    <button @click="store.increment()" class="increment">increment</button>
  </div>
</template>

<style scoped>
  .count-number{
    font-size: 160px;
    text-align: center;
    margin-bottom: 40px;
    font-weight: bold;
  }
  button{
    border: none;
    padding: 10px 15px;
    font-size: 16px;
    cursor: pointer;
  }
  button.decrement{
    background: pink;
  }
  button.reset{
    background: antiquewhite;
  }
  button.increment{
    background: lightblue;
  }
</style>
