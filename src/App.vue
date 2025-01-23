<script setup>

import {ref} from "vue";

let id = 1

const posts = ref([
])


const newPost = ref('')
function addPost() {
    if (newPost.value === '' || newPost.value.length < 3) {
        alert('Минимум 3 символа!')
    } else {
        posts.value.push({id: id++, text: newPost.value})
    }
}

</script>

<template>
    <div class="container">
        <div class="box"  v-for="post in posts" :key="post">
            <h1> {{ post.id }} </h1>
            <p> {{ post.text }} </p>
        </div>
    </div>

    <div class="post-form">
        <p>Форма поста</p>
        <input v-model="newPost" type="text">
        <button @click="addPost" type="submit">Add</button>
    </div>


</template>

<style scoped>

    .post-form {
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 300px;
        height: 300px;
        display: flex;

    }

    .container {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .box {
        margin: 10px;
        display: flex;
        background-color: greenyellow;
        width: 100px;
        height: 100px;
        border: 2px solid;
        border-radius: 10px;
        justify-content: center;
        align-items: center;
    }
</style>
