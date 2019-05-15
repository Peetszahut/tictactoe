<template>
  <div id="app">
    <div v-if="state === 'login'">
      <Header />
      <Login v-on:goHome="newMethod($event)" />
      <Scores />
    </div>
    <div v-else-if="state === 'game'">
      <Header />
      <Gameboard :board-prop="gameSize" />
    </div>
    <div v-else>
      <Register />
    </div>
  </div>
</template>

<script>
import Login from './components/Login.vue'
import Scores from './components/Scores.vue'
import Register from './components/Register.vue'
import Gameboard from './components/Gameboard.vue'
import Header from './components/Header.vue'

export default {
  name: 'app',
  components: {
    Login,
    Scores,
    Register,
    Gameboard,
    Header
  },
  data (){
    return {
      gameSize: 4,
      state: 'login'
    }
  },
  methods: {
    newMethod(updateState) {
      this.state = updateState;
      console.log(this.state)
    }
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
