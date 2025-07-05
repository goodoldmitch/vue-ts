<script setup lang="ts">
    import type { Post } from '@/types/post'

    defineProps<{post: Post}>()
</script>

<template>
    <div class="post-item">
        <h3>{{ post.title }}</h3>
        <p>
            {{ post.body }}
        </p>
        <small>{{ post.id }}</small>
    </div>
</template>

<style scoped>
    .post-item{
        position: relative;
        background: #fff;
        border-radius: 20px;
        padding: 25px;
        transition: all 300ms ease-in-out;
    }
    .post-item:hover{
        box-shadow: 0 0 10px rgba(256,256,256,.8);
        transform: scale(1.05);
    }
    h3{
        font-size: 24px;
        margin-bottom:20px;
    }
    p{
        line-height: 1.1;
    }
    small{
        position: absolute;
        bottom: 10px;
        right: 10px;
        font-size: 10px;
        font-weight: bold;
    }
</style>