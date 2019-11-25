
<template>
    <div id="post-page">
        {{this.post.title}}
    </div>
</template>

<script>
import posts from '~/data/posts.json'

export default {
    name: 'post-page',
    data() {
        return {
            posts: posts,
            post: []
        }
    },
    created() {
        this.post = this.posts.find(post => post.id == (this.$route.params.id));
    }
}
</script>

<style scoped>

</style>