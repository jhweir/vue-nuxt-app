<template>
    <div id="wall">

        <h1>Wall</h1>

        <div id="search-posts">
            <input class="text-input" v-model="searchText" @keyup="searchPosts" placeholder="Search posts..."/>
            <!--<button @click="searchPosts">Search posts</button>-->
        </div>

        <div id="submit-post">
            <input class="text-input" v-model="newPost" placeholder="Post title..."/>
            <button class="button" @click="submitPost">Submit post</button>
        </div>

        <div id="filters">
            <button class="button" @click='orderById'>Sort by Id</button>
            <button class="button" @click='orderByLikes'>Sort by Likes</button>
            <button class="button" @click='orderByComments'>Sort by Comments</button>
        </div>

        <div id="posts">
            <post v-for="post in posts"
                :key="post.id"
                :id="post.id"
                :title="post.title"
                :description="post.description"
                :likes="post.likes"
                :comments="post.comments"
                :tags="post.tags"
                :visible="post.visible"
                @addLike="addLike($event)"
                @addComment="addComment($event)"
                @tag="addTag($event)"
            />
        </div>

    </div>
</template>

<script>
import post from '~/components/post.vue'
import posts from '~/data/posts.json'

export default {
    components: {
        post
    },
    data() {
        return {
            posts: posts,
            newPost: '',
            searchText: ''
        }
    },
    methods: {
        searchPosts: function() {
            for (var i = 0; i < this.posts.length; i++) {
                if (this.posts[i].title.toLowerCase().includes(this.searchText.toLowerCase())) {
                    this.posts[i].visible = true;
                } else {
                    this.posts[i].visible = false;
                }
            }
        },
        submitPost: function() {
            if (this.newPost !== '') {
                this.posts.push({
                    id: this.posts.length + 1,
                    title: this.newPost,
                    description: '',
                    likes: 0,
                    comments: 0,
                    tags: [],
                    visible: true
                })
            }
            this.newPost = ''
        },
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
        addLike: function(addLike) {
            this.posts.find(post => post.id === addLike).likes++
        },
        addComment: function(addComment) {
            this.posts.find(post => post.id === addComment).comments++
        },
        addTag: function(tag) {
            this.posts.find(post => post.id === tag.id).tags.push('#' + tag.newTag)
        }
    }
}
</script>

<style>
#wall {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

#search-posts {
    margin: 10px 0;
}

#submit-post {
    margin: 10px 0;
}

#filters {
    margin: 10px 0;
}


#posts {
    width: 600px;
}
</style>
