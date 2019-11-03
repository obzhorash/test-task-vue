<template>
  <div id="app">
    <scene></scene>
    <keyboard></keyboard>
  </div>
</template>

<script>
import Scene from './components/Scene.vue'
import Keyboard from './components/Keyboard.vue'


export default {
  name: 'app',
  components: {
    Scene,
    Keyboard
  }
}
</script>

<style>
    #app {
      display: flex;
      align-items: center;
      justify-content: center;
    }

</style>