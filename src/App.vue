<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// static import works
//import HelloWorld from './components/HelloWorld.vue'

// dynamic import doesn't work
const HelloWorld = (resolve) => {
  import(/* webpackChunkName: "helloworld" */'./components/HelloWorld.vue')
  .then(AsyncComponent => {
    resolve(AsyncComponent.default);
  });
}

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
