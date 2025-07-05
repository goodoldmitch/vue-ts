<script setup lang="ts">
    import type { Post } from '@/types/post'
    import PostItem from './PostItem.vue';
    
    defineProps<{
        blogArray: Post[],
        isLoading: boolean
    }>();
</script>

<template>
    <section class="posts">
        <div class="container">
            <div class="posts-list" v-if="!isLoading">
                <post-item v-for="postItem in blogArray" :post="postItem" :key="postItem.id"></post-item>
            </div>
            <div class="loading" v-else>Loading...</div>
        </div>
  </section>
</template>

<style scoped>
 .posts{
    padding: 60px 0;
 }
 .posts-list{
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 30px;
 }
 .loading{
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    animation: blinking 1.5s infinite;
    color: #fff;
    font-size: 24px;
 }

 @keyframes blinking {
    0%{
        opacity: 0.5;
    }
    50%{
        opacity: 1;
    }
    100%{
        opacity: 0.5;
    }
 }
 @media screen and (max-width: 1000px) {
    .posts-list{
        grid-template-columns: repeat(2, 1fr);
    }
 }
</style>