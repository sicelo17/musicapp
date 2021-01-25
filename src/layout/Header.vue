<template>
    <div>
        <header class="header">
      <h1>My Music</h1>
      <div id="nav">
        <router-link to="/">Music</router-link> |
        <router-link to="/about">About</router-link>
      </div>
    </header>
    </div>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    .header {
    display: block;
    justify-content: center;
    align-items: center;
    padding: 10px;
    background-color: #212121;
    color: #fff;
    }

    .header a {
        color: #fff;
        padding-right: 5px;
        text-decoration: none;
    }
</style>