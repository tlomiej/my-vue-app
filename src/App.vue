<template>
  <img alt="Vue logo" src="./assets/logo.png">
<HelloWorld msg="Welcome to Your Vue.js App"/> 
<FirstComp msg="Nazwa przycisku"></FirstComp>


</template>

<script>
import FirstComp from './components/FirstComp.vue'

export default {
  name: 'App',
  components: {
    FirstComp
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
