<template>
  <div id="app">
    <h1 class="text-primary">Welcome to the Spartacus Workout Counter</h1>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'App',
  created() {
    document.title = 'Spartacus Workout | Counter'
  },
})
</script>

<style lang="scss">
@import './assets/scss/main';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  display: flex;
  color: $white;
  width: 100%;
  height: 100%;
  padding: 20px;
}
</style>
