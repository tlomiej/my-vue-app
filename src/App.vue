<template>
  <img alt="Vue logo" src="./assets/logo.png">
<HelloWorld msg="Welcome to Your Vue.js App"/> 
<FirstComp msg="Nazwa przycisku"></FirstComp>
<VueFor></VueFor>


</template>

<script>
import FirstComp from './components/FirstComp.vue'
import VueFor from './components/VueFor.vue'

export default {
  name: 'App',
  components: {
    FirstComp,
    VueFor
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
