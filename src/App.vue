<template>
  <div id="app" class="d-flex pa-20 flex-column">
    <div class="header justify-center">
      <h2 class="ma-0 text-center">
        <span class="text-secondary">Spartacus Workout</span> Counter
      </h2>
    </div>

    <main class="flex-grow-1 d-flex flex-column justify-center align-center">
      <Main />
    </main>

    <div class="footer d-flex justify-center">
      <p class="ma-0">Made with <span class="text-primary">♥</span> by <a href="https://emachado.pt" target="_blank"
          rel="noopener noreferrer">emachado.pt</a></p>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

import Main from './components/Main.vue'

export default Vue.extend({
  name: 'App',
  components: {
    Main,
  },
  created() {
    document.title = 'Spartacus Workout | Counter'
  },
})
</script>

<style lang="scss">
@import './assets/scss/main';

#app {
  color: $white;
  width: 100%;
  height: 100%;
}

.start-button {
  font-size: 3rem;
}
</style>
