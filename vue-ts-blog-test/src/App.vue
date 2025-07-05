<script setup lang="ts">
import Header from '@/components/Header.vue'
import PostsList from '@/components/PostsList.vue'
import Pagination from '@/components/Pagination.vue'
import axios from 'axios'
import { ref, onMounted } from 'vue'

const mainHeader = 'Testing blog layout with axios'
const blogArray = ref([]);
const postsPerPage = 8;
const currentPage = ref(1);
const isLoading = ref(true);

let postsTotal: number;
let pagesNumber: number;

async function fetchPosts(postsAmount: number, page: number) {
  try {
    const response = await axios.get('https://jsonplaceholder.typicode.com/posts', {
      params: {
        _limit: postsAmount,
        _page: page
      },
    })

    setTimeout(()=>{
      blogArray.value = response.data;
      isLoading.value = false
    }, 1000)

    postsTotal = response.headers['x-total-count'];

    pagesNumber = Math.ceil(postsTotal / postsPerPage);

  } catch (error) {
    throw new Error('Error')
  }
}

onMounted(() => {
  fetchPosts(postsPerPage, currentPage.value)
})

function switchPage(switchPage: number){
  isLoading.value = true;
  currentPage.value = switchPage;
  fetchPosts(postsPerPage, currentPage.value);
  
}
</script>

<template>
  <Header :mainHeader="mainHeader" />
  <PostsList :blogArray="blogArray" :isLoading="isLoading"/>
  <Pagination 
    :pagesNumber="pagesNumber" 
    :currentPage="currentPage" 
    @switchPage="switchPage" 
    :isLoading="isLoading"
  />
</template>

<style scoped></style>
