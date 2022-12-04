<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/main">Pokedex</router-link>
  </nav>
  <router-view />
</template>

<style>
body {
  margin: 0;
  background-image: linear-gradient(
    to right,
    #83bf97,
    #deeb90,
    #f2c68e,
    #db3642
  );
}

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
