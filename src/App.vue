<template>
  <div id="app">
    <nav>
      <router-link to="/screen1">Screen 1</router-link> |
      <router-link to="/screen2">Screen 2</router-link> |
      <router-link to="/screen3">Screen 3</router-link>
    </nav>
    <h2>I am {{ socketId }}</h2>
    <router-view/>
    <h2>Messages</h2>
    <div v-for="message, id in messages" :key="id">
        {{message}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
      return {
          messages: [],
          socketId: ''
      }
  },
  components: {
  },
  sockets: {
      connect() {
        this.socketId = this.$socket.id
      },
      serverMessage (arg) {
          this.messages.push(arg)
      },
      serverMessages (arg) {
        this.messages = arg
      }
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
