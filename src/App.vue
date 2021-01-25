<template>
  <Header />
  <router-view/>
</template>

<script>
import Header from "./layout/Header"
export default {
  name: "App",
  components: {
    Header
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 5px;
}

#nav a {
  font-weight: bold;
  color: #fff;
}

#nav a.router-link-exact-active {
  color: #714ae4;
  text-decoration: underline;
  transition: .5s;
}
</style>
