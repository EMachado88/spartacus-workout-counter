<template>
  <main class="flex-grow-1 d-flex flex-column justify-center align-center">
    <div class="text-center">
      <span
        v-if="!workoutStarted"
        class="start-button btn btn-primary"
        @click="startWorkout"
        @keypress="startWorkout"
      >
        Start
      </span>

      <div v-else>
        <h3 class="text-96">{{ counter }}</h3>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'MainComponent',
  data() {
    return {
      workoutStarted: false,
      exerciseDuration: 60,
      restDuration: 60,
      rounds: 3,
      restBetweenRounds: 180,
      counter: 0,
    }
  },
  methods: {
    startWorkout() {
      this.workoutStarted = true
      this.counter = this.exerciseDuration

      for (let i = 1; i <= this.exerciseDuration; i += 1) {
        setTimeout(() => {
          this.counter -= 1
        }, i * 1000)
      }
    },
  },
})
</script>
