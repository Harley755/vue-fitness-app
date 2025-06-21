<template>
  <Teleport to="#portal">
    <div class="portal-container">
      <div
        class="portal-underlay"
        role="button"
        tabindex="0"
        @click="handleCloseModal"
      ></div>
      <div class="portal-content">
        <slot />
      </div>
    </div>
  </Teleport>
</template>

<script lang="ts">
import type { PropType } from 'vue'

export default {
  props: {
    handleCloseModal: {
      type: Function as PropType<(event: MouseEvent) => void>,
    },
  },
}
</script>

<style scoped>
.portal-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}
.portal-underlay {
  position: absolute;
  opacity: 0.7;
  inset: 0;
  z-index: 1000;
  border: none;
  padding: 0;
  background-color: rgba(0, 0, 0, 0.5);
}
.portal-content {
  position: relative;
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  z-index: 1001;
  max-width: 600px;
  width: 100%;
}
.portal-content h2 {
  margin-top: 0;
}
.portal-content p {
  margin-bottom: 0;
}
.portal-content button {
  margin-top: 10px;
}
.portal-content .close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
}
.portal-content .close-button:hover {
  color: red;
}
.portal-content .close-button:focus {
  outline: none;
}
.portal-content .close-button:active {
  transform: scale(0.95);
}
</style>
