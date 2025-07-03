<script setup lang="ts">
import { ref, onMounted } from 'vue';

  interface Post{
    id: number,
    userId: number,
    body: string,
    title: string,
  }

  const postList = ref<Post[]>([]);

  async function getPosts(){
    try{
      const response = await fetch('https://jsonplaceholder.typicode.com/posts');
      if(!response.ok){
       throw new Error(response.status.toString());
      }
      postList.value = await response.json();
      console.log(postList);
    }  
    catch(error){
      alert(error);
    }
  }

  onMounted(getPosts)
  
</script>

<template>
  <div class="posts">
    <div v-for="post in postList" :key="post.id">
      <div class="post-item">
        <h3>{{ post.title }}</h3>
        <p>{{ post.body }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .posts{
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
  }
</style>
