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

function deletePost(postId) {
    const index = posts.value.findIndex(post => post.id === postId);
    if (index !== -1) {
        posts.value.splice(index, 1);
    }
}

</script>

<template>
    <div class="container">
        <div class="form-container">
            <div class="form-post">
                <input v-model="newPost" type="text" placeholder="название...">
                <button class="form-button" @click="addPost" type="submit">добавить</button>
            </div>
        </div>
    </div>



    <div class="content">
        <div class="posts"  v-for="post in posts" :key="post">
            <div class="post">
                <h1> {{ post.id }} </h1>
                <p> {{ post.text }} </p>
                <button @click="deletePost(post.id)">удалить</button>
            </div>
        </div>
    </div>

</template>

<style scoped>
     input {
         width: 280px;
         height: 33px;
         background-color: #f6e4c1;
         border: none;
         outline: none;
         border-radius: 50px;
         padding-left: 10px;
         box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
     }
     .form-button {
         display: inline-block;
         margin-top: 14px;
         width: 140px;
         height: 34px;
         font-family: 'Helvetica', 'Arial', sans-serif;
         text-align: center;
         font-size: 17px;
         padding: 0;
         line-height: 30px;
         background-color: #ffb74d;
         color: #fff;
         border-radius: 7px;
         border: none;
         cursor: pointer;
         position: relative;
         transition: transform ease-in 0.1s, background-color ease-in 0.25s;
         box-shadow: 0 2px 25px rgba(255, 183, 77, 0.7);
     }

     .form-button:active {
         transform: scale(0.9);
         background-color: #ffb74d; /* Темнее на 5% */
         box-shadow: 0 2px 25px rgba(255, 0, 130, 0.2);
     }

    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 330px;
    }
    .form-container {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 380px;
        height: 330px;
        border-radius: 18px;

    }
    .form-post {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        width: 300px;
        height: 300px;

    }

    .content {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
    }
    .posts {
        display: flex;
        flex-direction: column;
        margin: 10px;
        background-color: greenyellow;
        border: 2px solid;
        border-radius: 10px;
        justify-content: center;
        align-items: center;
    }
    .post {
        width: 150px;
        height: 150px;
        margin-left: 10px;
        text-align: center;
    }
</style>
