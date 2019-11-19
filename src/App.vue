<template>
  <div id="app">
    <ul>
      <li v-for="(item, index) in users" :key="index">
        {{item.name}}
      </li>
    </ul>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <HelloWorld msg="Welcome to My Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'
export default {
  name: 'app',
  data() {
    return {
      users: []
    }
  },
  components: {
    HelloWorld
  },
  mounted() {
    axios.get('/api/users').then(res => {
      this.users = res.data
    })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
