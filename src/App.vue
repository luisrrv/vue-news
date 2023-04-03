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
    // console.log('APP');
  }
}
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: #272a2e;
  color: #eeeeee;
  transition: 200ms;
  &.light {
    filter:invert(1);
    background-color: #eeeeee;
    color: #272a2e;
  }
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
