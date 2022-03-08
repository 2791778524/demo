<template>
  <div id="app">
    <!-- <HelloWorld /> -->
    <!-- <table-view-vue /> -->
    <Cascader />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TableViewVue from './components/TableViewVue.vue'
import Cascader from './components/Cascader.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    TableViewVue,
    Cascader
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
