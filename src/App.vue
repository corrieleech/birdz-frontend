<script>
export default {
  data: function () {
    return {
      isLoggedIn: !!localStorage.jwt,
      birder: localStorage.getItem("birder"),
    };
  },
  watch: {
    $route: function () {
      this.isLoggedIn = !!localStorage.jwt;
      this.birder = localStorage.getItem("birder");
    },
  },
};
</script>

<template>
  <nav>
    <router-link to="/">Home</router-link>
    |
    <router-link to="/about">About</router-link>
    |
    <router-link to="/signup">Sign Up</router-link>
    |
    <router-link to="/login">Log In</router-link>
    |
    <router-link to="/logout">Log Out</router-link>
    |
    <router-link to="/checklists/1">Checklist</router-link>
    |
    <router-link to="/checklists/new">Create</router-link>
  </nav>
  <router-view />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
