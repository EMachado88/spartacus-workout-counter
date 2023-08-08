<template>
  <div id="app" class="pa-18">
    <h1 class="text-white">Welcome to the <span class="text-primary">Spartacus Workout</span> <span
        class="text-secondary">Counter</span></h1>
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
  text-align: center;
  display: flex;
  color: $white;
  width: 100%;
  height: 100%;
}
</style>
