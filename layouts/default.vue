<template>
    <div id="layout">
        <navbar />
        <nuxt />
    </div>
</template>

<script>
import navbar from '~/components/navbar.vue'

export default {
    components: {
        navbar
    }
}
</script>

<style lang="less">
html {
    font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
        Roboto, 'Helvetica Neue', Arial, sans-serif;
    font-size: 16px;
    word-spacing: 1px;
    -ms-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

a {
    text-decoration: none;

    &:visited {
        color: black;
    }
}

</style>
