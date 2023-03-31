<template>
  <NavBar title />
  <CounterComp string="nav text" />
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
</template>

<script>
import CounterComp from './components/CounterComp.vue'
import NavBar from './components/NavBar.vue'

export default {
  name: 'App',
  components: {
    CounterComp,
    NavBar
  },
  created(){
    console.log('APP');
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
  margin-top: 60px;
}
</style>
