<template>
  <div class="card border-0 shadow-sm w-100">
    <div class="card-body">
      <h5 class="card-title mb-3 fw-semibold">Welcome Smoldier</h5>
      <p class="card-text mb-2 text-justify">Daily Tips :</p>
      <p class="mb-4">{{ randomGymHealthFact }}</p>
      <button class="btn btn-success btn-lg fw-bold px-4">
        Start Workout &rarr;
      </button>
    </div>
  </div>

  <Grid />
</template>

<script lang="ts">
import { gymHealthFacts } from '../../utils/index.ts'
import Grid from '../Grid.vue'

export default {
  components: {
    Grid,
  },
  data() {
    return {
      // Data properties can be added here if needed
      randomGymHealthFact: '',
    }
  },

  methods: {
    // Method to fetch a random gym health fact
    getRandomGymHealthFact() {
      const randomIndex = Math.floor(Math.random() * gymHealthFacts.length)
      this.randomGymHealthFact = gymHealthFacts[randomIndex]
    },
  },

  mounted() {
    this.getRandomGymHealthFact()
  },
}
</script>

<style scoped></style>
