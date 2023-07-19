<script setup>
import UseClipboard from './components/useClipboard.vue'
import UseFullscreen from './components/useFullscreen.vue'
</script>

<template>
  <UseClipboard />
  <UseFullscreen />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
