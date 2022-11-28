<template>
  <div id="app">
    <TestComponent/>
  </div>
</template>

<script>
import TestComponent from './components/TestComponent'

export default {
  name: 'App',
  components: {
    TestComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
