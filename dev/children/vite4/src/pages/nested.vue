<template>
  <div class="nested-container">
    <h2>子应用 B (vite4) - 嵌套加载子应用 C</h2>
    <p>当前路径: {{ $route.fullPath }}</p>
    <micro-app-vite4
      name="vite2-app"
      url="http://localhost:7001/"
      iframe
      baseroute="/nested"
      @created="handleCreated"
      @mounted="handleMounted"
      @error="handleError"
    ></micro-app-vite4>
  </div>
</template>

<script setup>
import { onMounted } from 'vue'

const handleCreated = () => {
  console.log('✅ [子应用 B] 子应用 C (vite2) created')
}

const handleMounted = () => {
  console.log('✅ [子应用 B] 子应用 C (vite2) mounted')
}

const handleError = (e) => {
  console.error('❌ [子应用 B] 子应用 C (vite2) error:', e)
}

onMounted(() => {
  console.log('📍 [子应用 B] nested 页面已挂载')
})
</script>

<style scoped>
.nested-container {
  padding: 20px;
  background-color: #e3f2fd;
  min-height: 100vh;
}

h2 {
  color: #1976d2;
  margin-bottom: 10px;
}

p {
  color: #666;
  margin-bottom: 20px;
}

micro-app-vite4 {
  display: block;
  width: 100%;
  height: calc(100vh - 200px);
  border: 2px solid #1976d2;
  border-radius: 4px;
}
</style>
