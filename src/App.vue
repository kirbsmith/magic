<template>
  <h1 class="text-5xl pb-8 font-sans">Magic: The Gathering Online Game</h1>
  <NavComponent />
  <ChatComponent />
  <PlayerComponent />
</template>

<script>
import NavComponent from './components/NavComponent.vue'
import ChatComponent from './components/ChatComponent.vue'
import PlayerComponent from './components/PlayerComponent.vue'

export default {
  name: 'App',
  components: {
    NavComponent,
    ChatComponent,
    PlayerComponent
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
