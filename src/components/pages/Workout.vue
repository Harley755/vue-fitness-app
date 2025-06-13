<template>
  <portal></portal>
  <div id="workout-select">
    <div class="row d-flex justify-content-between g-4">
      <div class="card border-0 shadow-sm col-md-2 mx-2">
        <div class="card-body">
          <!-- Titre et icône sur la même ligne -->
          <div class="d-flex justify-content-between align-items-center mb-3">
            <h4 class="card-title fw-semibold mb-0">
              Day {{ selectWorkout < 9 ? '0' + selectWorkout : selectWorkout }}
            </h4>
            <span>
              <font-awesome-icon :icon="['fas', 'dumbbell']" />
              <font-awesome-icon :icon="['fas', 'weight-hanging']" />
              <font-awesome-icon :icon="['fas', 'bolt']" />
            </span>
          </div>
          <div class="d-flex justify-content-between align-items-center mb-2">
            <p class="card-text text-justify mb-0">{{ 'Push' }} Workout</p>
          </div>
        </div>
      </div>
    </div>

    <div id="workout-grid" class="mt-4">
      <table class="table table-striped table-hover">
        <thead>
          <tr>
            <th>Warmup</th>
            <th>Sets</th>
            <th>Reps</th>
            <th>Weights</th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="(w, wIdx) in warmup" :key="wIdx" class="hover-row">
            <td>
              {{ w.name }}
              <font-awesome-icon
                icon="fa-solid fa-circle-question"
                class="question-icon"
              />
            </td>
            <td>{{ w.sets }}</td>
            <td>{{ w.reps }}</td>
            <td>
              <input
                type="number"
                placeholder="14 Kg"
                class="form-control"
                id="numberInput"
                disabled
              />
            </td>
          </tr>
        </tbody>
      </table>

      <table class="table table-striped table-hover mt-3">
        <thead>
          <tr>
            <th>Workout</th>
            <th>Sets</th>
            <th>Reps</th>
            <th>Weights</th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="(w, wIdx) in workout" :key="wIdx" class="hover-row">
            <td>
              {{ w.name }}
              <font-awesome-icon
                icon="fa-solid fa-circle-question"
                class="question-icon"
              />
            </td>
            <td>{{ w.sets }}</td>
            <td>{{ w.reps }}</td>
            <td>
              <input
                type="number"
                placeholder="14 Kg"
                class="form-control"
                id="numberInput"
              />
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="d-flex mt-5">
      <button class="btn btn-success">Save & Exit</button>
      <button class="btn btn-secondary mx-3">Complete</button>
    </div>
  </div>
</template>

<script lang="ts">
import { workoutProgram } from '../../utils/index.ts'
import Portal from '../Portal.vue'

type WorkoutDay = {
  warmup: { name: string; sets: number; reps: number }[]
  workout: { name: string; sets: number; reps: number }[]
}

export default {
  components: {
    Portal,
  },
  data() {
    return {
      program: workoutProgram as Record<number, WorkoutDay>,
      workOutTypes: ['Push', 'Pull', 'Legs'],
      selectWorkout: 4,
    }
  },
  computed: {
    selectedDay() {
      // On récupère l'objet du jour sélectionné
      return this.program[this.selectWorkout] || {}
    },
    workout() {
      return this.selectedDay.workout || []
    },
    warmup() {
      return this.selectedDay.warmup || []
    },
  },
  mounted() {
    console.log(workoutProgram)
  },
}
</script>

<style scoped>
.question-icon {
  opacity: 0;
  transition: opacity 0.2s;
  margin-left: 8px;
  cursor: pointer;
}
.hover-row:hover .question-icon {
  opacity: 1;
}
</style>
