<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
     <h1>Vue Async Component Demo</h1>
    <div>
      <List v-if="show" />
      <button @click="show = !show">Show</button>
    </div>
  </div>
</template>

<script>
import Error from './components/Error'
import Loading from './components/Loading'

const List = () => ({
  component: import(/* webpackChunkName: "list" */ './components/List.vue'),
  loading: Loading,
  error: Error,
  timeout: 30000
})

export default {
  name: 'App',
  data() {
    return {
      show: false
    }
  },
  components: {
    List
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
