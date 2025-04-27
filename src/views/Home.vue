<template>
  <div class="layout">
    <!-- 导航栏 -->
    <nav class="navbar">
      <div class="logo">ASLP 可视化系统</div>
      <ul class="nav-links">
        <li><router-link to="/" class="active">首页</router-link></li>
        <li><router-link to="/overview">数据分析</router-link></li>
        <li><router-link to="/visualization">可视化</router-link></li>
        <li><router-link to="/analysis">分析报告</router-link></li>
      </ul>
    </nav>

    <!-- 主要内容区域 -->
    <main class="main-content">
      <div class="welcome-section">
        <h1>欢迎使用 ASLP 可视化系统</h1>
        <p>这是一个用于数据分析和可视化的平台</p>
      </div>

      <!-- 数据卡片区域 -->
      <div class="card-container">
        <router-link to="/overview" class="card">
          <h3>数据总览</h3>
          <p>查看所有数据统计</p>
        </router-link>
        <router-link to="/analysis" class="card">
          <h3>分析报告</h3>
          <p>生成数据分析报告</p>
        </router-link>
        <router-link to="/visualization" class="card">
          <h3>可视化图表</h3>
          <p>创建交互式图表</p>
        </router-link>
      </div>
    </main>
  </div>
</template>

<script setup>
import { useRouter } from "vue-router";
const router = useRouter();
</script>

<style scoped>
.layout {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.navbar {
  background-color: #2c3e50;
  padding: 1rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: white;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
}

.nav-links {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-links li {
  margin-left: 2rem;
}

.nav-links a {
  color: white;
  text-decoration: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.nav-links a:hover,
.nav-links a.active {
  background-color: #34495e;
}

.main-content {
  flex: 1;
  padding: 2rem;
  background-color: #f5f6fa;
}

.welcome-section {
  text-align: center;
  margin-bottom: 3rem;
}

.welcome-section h1 {
  color: #2c3e50;
  margin-bottom: 1rem;
}

.card-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  padding: 1rem;
}

.card {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
  cursor: pointer;
  text-decoration: none;
}

.card:hover {
  transform: translateY(-5px);
}

.card h3 {
  color: #2c3e50;
  margin-bottom: 0.5rem;
}

.card p {
  color: #666;
  margin: 0;
}
</style>
