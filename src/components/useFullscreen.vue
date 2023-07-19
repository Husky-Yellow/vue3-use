<script setup>
import { useFullscreen } from '@vueuse/core';
const { toggle, isFullscreen } = useFullscreen();
// 重新检查全屏状态
isFullscreen.value = !!(
  document.fullscreenElement ||
  document.webkitFullscreenElement ||
  document.mozFullScreenElement ||
  document.msFullscreenElement
);
</script>

<template>
  <h1 @click="toggle">
    点击切换，当是全屏时点击ESC时isFullscreen不会改变，因为fullscreenchange事件没有被触发
  </h1>
  <a href="https://vueuse.org/" target="_blank">{{
    isFullscreen ? '全屏' : '非全屏'
  }}</a>
</template>

<style></style>
