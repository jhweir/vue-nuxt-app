<template>
  <div id="container">
    <h2>Create new branch</h2>
    <div id="submit-branch">
        <input v-model="newBranch">
        <button v-on:click="submitBranch">Creat branch</button>
    </div>
    <button v-on:click='orderById'>Sort by Id</button>
    <button v-on:click='orderByLikes'>Sort by Likes</button>
    <button v-on:click='orderByComments'>Sort by Comments</button>
    <div v-bind:key="branch.id" v-for="branch in branches">
        <nuxt-link :to="'b/' + branch.slug">{{branch.title}}</nuxt-link>
        <h5>{{branch.description}}</h5>
        <h5>{{branch.likes}} Contained Likes</h5>
        <h5>{{branch.comments}} Contained Comments</h5>
        <button v-on:click="branch.likes++">Add like</button>
        <button v-on:click="branch.comments++">Add comment</button>
    </div>
  </div>
</template>

<script>
import branchData from '~/data/branches.json'

export default {
    name: 'branches',
    data() {
        return {
            branches: branchData,
            newBranch: ''
        }
    },
    methods: {
        orderById: function() {
            this.branches.sort((a, b) => {
                return (a.id > b.id) ? 1 : -1
            })
        },
        orderByLikes: function() {
            this.branches.sort((a, b) => {
                return (a.likes < b.likes) ? 1 : -1
            })
        },
        orderByComments: function() {
            this.branches.sort((a, b) => {
                return (a.comments < b.comments) ? 1 : -1
            })
        },
        submitBranch: function() {
            this.branches.push({
                id: this.branches.length + 1,
                title: this.newBranch,
                likes: 0,
                comments: 0
            })
            this.newBranch = ''
        }
    }
}
</script>

<style>
#submit-branch {
    padding: 20px;
}
</style>