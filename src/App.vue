<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <ProjectElement></ProjectElement>
  <HelloWorld></HelloWorld>
  <FirstComp msg="Nazwa przycisku"></FirstComp>
  <VueFor></VueFor>
  <DynamicBindings></DynamicBindings>
</template>

<script>
import FirstComp from "./components/FirstComp.vue";
import VueFor from "./components/VueFor.vue";
import DynamicBindings from "./components/DynamicBindings.vue";
import HelloWorld from "./components/HelloWorld.vue";
import ProjectElement from './components/ProjectElement.vue'

export default {
  name: "App",
  components: {
    FirstComp,
    VueFor,
    DynamicBindings,
    HelloWorld,
    ProjectElement,
  },
};
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
