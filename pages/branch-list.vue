<template>
    <div id="container">
        <h1>Branch list</h1>
        <branches />
    </div>
</template>

<script>
import branches from '~/components/branches.vue'

export default {
    components: {
        branches
    },
    head() {
        return {
            title: "Branch list",
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