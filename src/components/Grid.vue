<template>
  <section class="mt-5">Hello</section>
</template>

<script lang="ts">
import { workoutProgram } from '../utils'
export default {
  data() {
    return {
      program: { ...workoutProgram },
    }
  },

  mounted() {
    // Log the workout program to the console
    console.log(workoutProgram)
  },
}
</script>

<style scoped></style>
