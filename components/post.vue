<template>
    <div id="post" v-if="visible">
        <nuxt-link :to="'posts/' + id">
            <span class="post-title"> {{ title }} </span>
        </nuxt-link>
        <span class="post-description"> {{ description }} </span>
        <span> {{ likes }} Likes</span>
        <span> {{ comments }} Comments</span>
        <div class="tags">
            <div class="tag" v-for="tag in tags" :key="tag.id"> {{ tag }} </div>
        </div>
        <button @click="addLike">Add like</button>
        <button @click="addComment">Add comment</button>
        <input v-model="newTag" />
        <button @click="addTag">Add tag</button>
    </div>
</template>

<script>
export default {
    name: 'post',
    props: ['id', 'title', 'description', 'likes', 'comments', 'tags', 'visible'],
    data() {
        return {
            newTag: '',
        }
    },
    methods: {
        addLike: function() {
            this.$emit('addLike', this.id)
        },
        addComment: function() {
            this.$emit('addComment', this.id)
        },
        addTag: function() {
            if (this.newTag !== '') {
                this.$emit('tag', {'id': this.id, 'newTag': this.newTag});
                this.newTag = ''
            }
        }
    }
}
</script>

<style scoped>
.post-title {
    font-size: 24px;
}
.post-description {
    font-size: 16px;
}
.tags {
    display: flex;
    flex-direction: row;
}
.tag {
    background-color: #ddd;
    padding: 4px 10px;
    margin-right: 5px;
    border-radius: 5px;
}
</style>