<template>
  <header class="header justify-center">
    <h2 class="ma-0">
      <a class="logo" href="javascript:void(0)">
        <img class="w-100" src="img/icons/safari-pinned-tab.svg" alt="Spartacus Workout counter">
      </a>
    </h2>
  </header>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'HeaderComponent',
})
</script>

<style lang="scss">
.logo {
  display: block;
  max-width: 60px;
}
</style>
