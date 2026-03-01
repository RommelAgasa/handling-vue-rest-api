<template>
    <div>
        <button @click="getPosts">Load Posts</button>
    </div>
    <h3 v-if="errorMessage">
        {{ errorMessage }}
    </h3>
    <div v-for="post in posts" :key="post.id">
        <h3>{{ post.id }} - {{ post.title }}</h3>
        <p>{{  post.body }}</p>
        <hr>
    </div>
</template>

<script>

import axios from 'axios';

export default {
    name: 'PostList',
    data(){
        return {
            posts: [],
            errorMessage: ''
        }
    },
    methods: {
        getPosts(){
            axios.get('https://jsonplaceholder.typicode.com/posts')
                .then(response => {
                    this.posts = response.data;
                    console.log(this.posts);
                })
                .catch((error) => {
                    this.errorMessage = 'Failed to load posts';
                    console.error(error);
                });
        }
    }
}

</script>

<style scoped>

</style>