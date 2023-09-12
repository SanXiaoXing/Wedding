<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/>
  </div>
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


<!-- 增加樱花飘落效果 -->
<script>
export default {
  mounted() {
      const script = document.createElement('script');
      script.src = 'https://cdn.jsdelivr.net/gh/Fuukei/Public_Repository@latest/static/js/sakura-less.js';
      document.body.appendChild(script);
  }
}
</script>