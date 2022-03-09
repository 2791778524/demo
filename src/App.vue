<template>
  <div id="app">
    <!-- <HelloWorld /> -->
    <!-- <table-view-vue /> -->
    <Cascader />
    <!-- <TreeSelect /> -->
    <!-- <Commont /> -->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TableViewVue from './components/TableViewVue.vue'
import Cascader from './components/Cascader.vue'
import TreeSelect from './components/TreeSelect.vue'
import Commont from './components/Commont.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    TableViewVue,
    Cascader,
    TreeSelect,
    Commont
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
