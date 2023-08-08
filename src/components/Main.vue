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
        <h3 class="text-192" :class="`text-${counterColour}`">{{ counter }}</h3>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import Vue from 'vue'

const counterColours = {
  exercise: 'primary',
  rest: 'secondary',
  restRound: 'tertiary',
}

export default Vue.extend({
  name: 'MainComponent',
  data() {
    return {
      workoutStarted: false,
      exerciseDuration: 5,
      restDuration: 3,
      rounds: 3,
      restBetweenRounds: 10,
      counter: 0,
      counterColour: counterColours.exercise,
    }
  },
  methods: {
    async startWorkout() {
      this.workoutStarted = true

      // For each round
      for (let round = 1; round <= this.rounds; round += 1) {
        // Exercise
        this.counter = this.exerciseDuration
        this.counterColour = counterColours.exercise

        for (let second = 1; second <= this.exerciseDuration; second += 1) {
          await this.sleep(1000)
          this.counter -= 1
        }

        // Rest
        this.counter = this.restDuration
        this.counterColour = counterColours.rest

        for (let second = 1; second <= this.restDuration; second += 1) {
          await this.sleep(1000)
          this.counter -= 1
        }

        // Rest between rounds
        this.counter = this.restBetweenRounds
        this.counterColour = counterColours.restRound

        for (let second = 1; second <= this.restBetweenRounds; second += 1) {
          await this.sleep(1000)
          this.counter -= 1
        }
      }
    },
    async sleep(ms: number) {
      return new Promise((resolve) => setTimeout(resolve, ms))
    },
  },
})
</script>
