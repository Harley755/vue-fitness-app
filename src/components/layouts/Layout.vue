<template>
  <div class="layout-root">
    <header>
      <h1 class="display-5 container">Smolgram</h1>
    </header>

    <main>
      <slot></slot>
    </main>

    <footer>
      <p class="container">&copy; 2023 Smolgram</p>
      <p class="container">Made with by Brice GOUDALO</p>
    </footer>
  </div>
</template>

<script lang="ts">
export default {}
</script>

<style scoped>
.layout-root {
  min-width: 100vh;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
header {
  background-color: #f8f9fa;
}

main {
  flex: 1 0 auto;
}
footer,
header {
  background-color: #f8f9fa;
  text-align: left;
  padding: 1rem;
}
</style>
