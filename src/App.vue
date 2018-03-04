<template>
  <div id="app">
    <load-more></load-more>
  </div>
</template>

<script>
import LoadMore from './components/LoadMore'

export default {
  name: 'App',
  components: {
    LoadMore
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  overflow: scroll;
  height: 100%;
}
</style>
