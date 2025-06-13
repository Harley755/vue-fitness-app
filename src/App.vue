<template>
  <Layout>
    <div class="container py-5">
      <Welcome v-if="selectedDisplay === 1" />
      <Dashboard v-if="selectedDisplay === 2" />
      <Workout v-if="selectedDisplay === 3" />
    </div>
  </Layout>
</template>

<script lang="ts">
import Welcome from './components/pages/Welcome.vue'
import Layout from './components/layouts/Layout.vue'
import Dashboard from './components/pages/Dashboard.vue'
import Workout from './components/pages/Workout.vue'

export default {
  components: {
    Welcome,
    Layout,
    Dashboard,
    Workout,
  },

  data() {
    return {
      selectedDisplay: 3,
    }
  },
  methods: {
    // Methods can be added here if needed
  },
  mounted() {
    // Lifecycle hook for when the component is mounted
  },
}
</script>

<style scoped></style>
