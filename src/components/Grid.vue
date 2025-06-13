<template>
  <section class="mt-5">
    <div class="row d-flex justify-content-between g-4">
      <div
        v-for="(workout, index) in Object.keys(program)"
        :key="index"
        class="card border-0 shadow-sm col-md-2 mx-2"
      >
        <div class="card-body">
          <!-- Titre et icône sur la même ligne -->
          <div class="d-flex justify-content-between align-items-center mb-3">
            <h4 class="card-title fw-semibold mb-0">
              Day {{ index < 9 ? '0' + (index + 1) : index + 1 }}
            </h4>
            <span>
              <font-awesome-icon
                :icon="['fas', 'dumbbell']"
                v-if="index % 3 === 0"
              />
              <font-awesome-icon
                :icon="['fas', 'weight-hanging']"
                v-if="index % 3 === 1"
              />
              <font-awesome-icon
                :icon="['fas', 'bolt']"
                v-if="index % 3 === 2"
              />
            </span>
          </div>
          <div class="d-flex justify-content-between align-items-center mb-2">
            <p class="card-text text-justify mb-0">
              {{ workOutTypes[index % 3] }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { workoutProgram } from '../utils'
export default {
  data() {
    return {
      program: { ...workoutProgram },
      workOutTypes: ['Push', 'Pull', 'Legs'],
    }
  },

  mounted() {
    // Log the workout program to the console
    console.log(workoutProgram)
  },
}
</script>

<style scoped></style>
