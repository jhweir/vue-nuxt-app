<template>
  <div id="navbar">
    <nuxt-link to="/">
        <img class="navbar-icon" src="~/assets/icons/home-02.svg"/>
    </nuxt-link>

    <nuxt-link to="/about">
        <img class="navbar-icon" src="~/assets/icons/about-01.png"/>
    </nuxt-link>

    <nuxt-link to="/wall">
        <img class="navbar-icon" src="~/assets/icons/wall-05.png"/>
    </nuxt-link>

    <!--<nuxt-link to="/branch-list">
        <img class="navbar-icon" src="~/assets/icons/node-01.png"/>
    </nuxt-link>-->
  </div>
</template>

<script>
export default {
  name: 'navbar'
}
</script>

<style scoped>
#navbar {
    width: 100%;
    height: 80px;
    background-color: #222;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
}

.navbar-icon {
    width: 30px;
    height: 30px;
    margin: 0 10px;
    filter: invert();
}
</style>