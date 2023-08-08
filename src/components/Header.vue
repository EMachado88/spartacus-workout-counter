<template>
  <header class="header d-flex justify-space-between">
    <a class="logo" href="javascript:void(0)">
      <img class="w-100" src="img/icons/safari-pinned-tab.svg" alt="Spartacus Workout counter">
    </a>
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
