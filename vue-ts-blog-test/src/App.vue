<script setup lang="ts">
import Header from '@/components/Header.vue'
import PostsList from '@/components/PostsList.vue'
import axios from 'axios'
import { ref, onMounted } from 'vue'

const mainHeader = 'Testing blog layout with axios'
const blogArray = ref([]);

async function fetchPosts() {
  try {
    const response = await axios.get('https://jsonplaceholder.typicode.com/posts', {
      params: {
        _limit: '10',
      },
    })

    // setTimeout(()=>{
      blogArray.value = response.data;
    // }, 3000)
    

  } catch (error) {
    throw new Error('Error')
  }
}

onMounted(() => {
  fetchPosts()
})
</script>

<template>
  <Header :mainHeader="mainHeader" />
  <PostsList :blogArray="blogArray"/>
</template>

<style scoped></style>
