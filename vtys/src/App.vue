<template>
    <RouterView />
</template>

<script>
export default{

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

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
    color: #2c3e50;
    text-decoration: none;
    padding: 10px;
    border-radius: 4px;
}

nav a.router-link-exact-active {
    color: white;
    background: crimson;
}
body {
  background-image: url('./assets/1847.jpg');
  background-color: rgba(1, 1, 1, 0.5);
}
</style>
