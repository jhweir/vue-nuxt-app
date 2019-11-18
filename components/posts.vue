<template>
  <div id="container">
    <h1>Posts</h1>
    <button v-on:click='orderById'>Sort by Id</button>
    <button v-on:click='orderByLikes'>Sort by Likes</button>
    <button v-on:click='orderByComments'>Sort by Comments</button>
    <h2>Create new post</h2>
    <input v-model="newPost">
    <button v-on:click="submitPost">Submit post</button>
    <div v-bind:key="post.id" v-for="post in posts">
        <h1>{{post.title}}</h1>
        <h5>{{post.description}}</h5>
        <h5>{{post.likes}} Likes</h5>
        <h5>{{post.comments}} Comments</h5>
        <button v-on:click="post.likes++">Add like</button>
        <button v-on:click="post.comments++">Add comment</button>
    </div>
  </div>
</template>

<script>
import posts from '~/data/posts.json'

export default {
    name: 'posts',
    data() {
        return {
            posts: posts,
            newPost: ''
        }
    },
    methods: {
        orderById: function() {
            this.posts.sort((a, b) => {
                return (a.id > b.id) ? 1 : -1
            })
        },
        orderByLikes: function() {
            this.posts.sort((a, b) => {
                return (a.likes < b.likes) ? 1 : -1
            })
        },
        orderByComments: function() {
            this.posts.sort((a, b) => {
                return (a.comments < b.comments) ? 1 : -1
            })
        },
        submitPost: function() {
            this.posts.push({
                id: this.posts.length + 1,
                title: this.newPost,
                likes: 0,
                comments: 0
            })
            this.newPost = ''
        }
    }
}

</script>

<style>
</style>