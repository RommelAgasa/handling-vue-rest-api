<template>
    <div>
        <form @submit.prevent="createPost">
            <div>
                <label for="userId">Post User Id</label>
                <input type="text" v-model="formData.userId" id="userId">
            </div>
            <div>
                <label for="title">Post Title</label>
                <input type="text" v-model="formData.title" id="title">
            </div>
            <div>
                <label for="body">Post Body</label>
                <input type="text" v-model="formData.body" id="body">
            </div>
            <button type="submit">Create Post</button>
        </form>
    </div>
</template>

<script>
    import axios from 'axios';
    export default {
        name: 'CreatePost',
        data() {
            return {
                formData: {
                    userId: '',
                    title: '',
                    body: ''
                }
            }
        },
        methods: {
            createPost(){
                axios.post(
                    'https://jsonplaceholder.typicode.com/posts', 
                    this.formData)
                    .then(response => {
                        console.log(response.data);
                    }).catch(error => {
                        console.error(error);
                    });
            }
        }
    }
</script>

<style scoped>
#create-post{
    margin-top: 30px;
}
</style>