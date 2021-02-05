<template>
  <div id="app">
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <Container></Container>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Container from "@/components/Container";

export default {
  name: 'App',
  components: {
    // HelloWorld
    Container
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
</style>
