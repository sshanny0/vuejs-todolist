<!-- javascript -->
<script setup lang="ts">
import AppHeader from './components/AppHeader.vue'
import Task from './components/Task.vue'
</script>

<!-- HTML -->
<template>
  <AppHeader/>
    <Task :isChecked="true">True Membuat Komponen dari Task!</Task>
    <Task :isChecked="false">False Membuat Komponen dari Task!</Task>
</template>

<!-- CSS -->
<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family:
  'Poppins',
  system-ui,
  -apple-system,
  BlinkMacSystemFont,
  'Segoe UI',
  Roboto, 'Oxygen',
  Ubuntu,
  Cantarell,
  'Open Sans',
  'Helvetica Neue',
  sans-serif;
}

body {
  background: #f3f4f6;
}

#app{
  min-height: 100vh;
  background: linear-gradient(135deg, #667eea, #764ba2 100%);
  padding: 2rem;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 1.2rem;
}
</style> <!--  SCOPED HANYA UNTUK DI APP SAJA -->
