<template>
  <div class="nested-test-container">
    <h1>三层嵌套测试 - 主应用 A</h1>
    <div class="info-box">
      <p>当前：主应用 A (main-vite, 端口 5000)</p>
      <p>加载：子应用 B (vite4, 端口 7002) - iframe 模式</p>
      <p>子应用 B 将加载：子应用 C (vite2, 端口 7001) - iframe 模式</p>
    </div>

    <div class="micro-app-wrapper">
      <micro-app
        name='vite4-nested'
        url='http://localhost:7002/micro-app/vite4/nested'
        iframe
        inline
        :data="microAppData"
        @mounted="handleMounted"
        @error="handleError"
      ></micro-app>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const microAppData = ref({
  from: '来自主应用 A 的数据'
})

const handleMounted = () => {
  console.log('✅ 子应用 B (vite4) 已挂载')
}

const handleError = (e: any) => {
  console.error('❌ 子应用 B (vite4) 加载错误:', e)
}
</script>

<style scoped>
.nested-test-container {
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  color: #2c3e50;
  border-bottom: 2px solid #42b983;
  padding-bottom: 10px;
}

.info-box {
  background: #f0f9ff;
  border: 1px solid #0ea5e9;
  border-radius: 8px;
  padding: 15px;
  margin: 20px 0;
}

.info-box p {
  margin: 8px 0;
  color: #0c4a6e;
}

.micro-app-wrapper {
  border: 3px solid #42b983;
  border-radius: 8px;
  padding: 10px;
  margin-top: 20px;
  min-height: 600px;
}
</style>
