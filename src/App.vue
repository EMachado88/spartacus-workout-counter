<template>
  <div id="app" class="d-flex pa-20 flex-column">
    <Header />

    <main class="flex-grow-1 d-flex flex-column justify-center align-center">
      <Main />
    </main>

    <Footer />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

import Header from './components/Header.vue'
import Main from './components/Main.vue'
import Footer from './components/Footer.vue'

export default Vue.extend({
  name: 'App',
  components: {
    Header,
    Main,
    Footer,
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
