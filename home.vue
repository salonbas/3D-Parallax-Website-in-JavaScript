<template>
  <div class="home-container">
    <Mountain />
  </div>
</template>

<script setup>
import Mountain from './src/section/Mountain.vue'
</script>

<style scoped>
.home-container {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  margin: 0;
  padding: 0;
}

/* 全域樣式重置 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body, html {
  height: 100%;
  overflow: hidden;
  font-family: 'Inter', sans-serif;
}
</style>