<template>
  <div>
    <Menu v-if="!type" v-model:type="type"></Menu>
    <Game v-else :animals="animals" :type="type" @gameEnd="gameEnd()"></Game>
  </div>
</template>

<script>
import animals from './animals.json';
import Game from './components/Game.vue';
import Menu from './components/Menu.vue';

export default {
  name: 'App',
  components: {
    Game, Menu
  },
  data() {
    return {
      animals: animals,
      type: null
    }
  },
  methods: {
    gameEnd() {
      this.type = null;
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