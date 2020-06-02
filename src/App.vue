<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>

    </div>
    <router-view/>
  </div>
</template>

<style>
body {
  background: rgb(30, 15, 48);
  display: flex;
  justify-content: center;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
      border: 5px dashed rgb(50, 42, 97);
      background: slateblue;
      padding: 1rem;
      margin: 0.667rem;
      font-weight: bold;
      text-align: center;
      min-width: 80vw;
  }

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #211c57;
}
</style>
