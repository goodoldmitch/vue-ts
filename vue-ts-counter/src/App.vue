<script setup lang="ts">
  import { ref } from 'vue';

  const countNumber  = ref(0);

  function increment(){countNumber.value++}
  function reset(){countNumber.value = 0}
  function decrement(){countNumber.value--}
</script>

<template>
  
  <h1>{{ countNumber }}</h1>
  <div class="buttons-block">
    <button @click="decrement()" class="decrement">decrement</button>
    <button @click="reset()" class="reset">reset</button>
    <button @click="increment()" class="increment">increment</button>
  </div>
</template>

<style scoped>
  h1{
    font-size: 160px;
    text-align: center;
    margin-bottom: 40px;
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
