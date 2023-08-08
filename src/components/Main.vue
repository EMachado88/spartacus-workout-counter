<template>
  <div class="text-center">
    <span
      class="start-button btn btn-primary"
      @click="startWorkout"
      @keypress="startWorkout"
      v-if="!workoutStarted"
    >
      Start
    </span>

    <div v-else>
      <h1>Workout started!</h1>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'MainComponent',
  data() {
    return {
      workoutStarted: false,
    }
  },
  methods: {
    startWorkout() {
      this.workoutStarted = true
    },
  },
})
</script>
