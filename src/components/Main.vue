<template>
  <main class="flex-grow-1 d-flex flex-column justify-center align-center">
    <div class="text-center">
      <div v-if="!workoutStarted">
        <div
          class="start-button btn btn-primary"
          @click="startWorkout"
          @keypress="startWorkout"
        >
          Start
        </div>

        <a
          href="https://www.menshealth.com/fitness/a20695613/the-spartacus-workout/"
          target="_blank"
          rel="noopener noreferrer"
          class="instructions-button d-block btn btn-secondary mt-20"
        >
          View the workout
        </a>
      </div>

      <div v-else class="counter-wrapper">
        <div class="d-flex flex-column">
          <div class="counter-title text-uppercase" :class="`text-${counterColour}`">
            <div class="text-bold text-48">{{ counterTitle }}</div>
            <div
              v-if="counterTitle === counterTitles.exercise"
              class="text-32 text-secondary"
            >
              {{ exercises[currentExercise] }}
            </div>
          </div>

          <div class="counter flex-grow-1">
            <span class="text-192" :class="`text-${counterColour}`">{{ counter }}</span>
          </div>
        </div>
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

const counterTitles = {
  exercise: 'Exercise',
  rest: 'Rest',
  restRound: 'Rest and hydrate',
}

export default Vue.extend({
  name: 'MainComponent',
  data() {
    return {
      workoutStarted: false,
      exercises: [
        'Goblet Squat',
        'Feet-Elevated Mountain Climber',
        'Single-Arm Kettlebell Swing',
        'T-Pushup',
        'Split Jump',
        'Dumbbell Row',
        'Single-Arm Dumbbell Side Lunge and Touch',
        'Pushup and Row',
        'Dumbbell Lunge and Rotation',
        'Dumbbell Push Press',
      ],
      currentExercise: 0,
      exerciseDuration: 60,
      restDuration: 120,
      rounds: 3,
      restBetweenRounds: 180,
      counter: 0,
      counterColours,
      counterColour: counterColours.exercise,
      counterTitles,
      counterTitle: counterTitles.exercise,
    }
  },
  methods: {
    async startWorkout(): Promise<void> {
      this.workoutStarted = true

      // Rounds
      for (let round = 1; round <= this.rounds; round += 1) {
        // Exercises
        for (let exercise = 0; exercise < this.exercises.length; exercise += 1) {
          this.currentExercise = exercise

          // Exercise
          this.counter = this.exerciseDuration
          this.counterColour = counterColours.exercise
          this.counterTitle = counterTitles.exercise

          for (let second = 1; second <= this.exerciseDuration; second += 1) {
            await this.sleep(1000)
            this.counter -= 1
          }

          // Rests
          this.counter = this.restDuration
          this.counterColour = counterColours.rest
          this.counterTitle = counterTitles.rest

          for (let second = 1; second <= this.restDuration; second += 1) {
            await this.sleep(1000)
            this.counter -= 1
          }
        }

        // Rests between rounds
        this.counter = this.restBetweenRounds
        this.counterColour = counterColours.restRound
        this.counterTitle = counterTitles.restRound

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
