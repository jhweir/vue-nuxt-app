<template>
    <div id="container">
        <h1>Wall</h1>
        <posts />
    </div>
</template>

<script>
import posts from '~/components/posts.vue'

export default {
    components: {
        posts
    },
    head() {
        return {
        title: "Wall",
        meta: [
            {
            hid: '...',
            name: '...',
            content: '...'
            }
        ]
        }
    }
}
</script>

<style>
#container{
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
