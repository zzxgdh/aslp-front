<template>
  <div class="data-overview">
    <h2 class="page-title">数据总览</h2>

    <!-- 数据统计卡片 -->
    <div class="stats-container">
      <div class="stat-card">
        <div class="stat-value">2,345</div>
        <div class="stat-label">总数据量</div>
      </div>
      <div class="stat-card">
        <div class="stat-value">98%</div>
        <div class="stat-label">准确率</div>
      </div>
      <div class="stat-card">
        <div class="stat-value">1,234</div>
        <div class="stat-label">已处理数据</div>
      </div>
      <div class="stat-card">
        <div class="stat-value">89%</div>
        <div class="stat-label">完成度</div>
      </div>
    </div>

    <!-- 数据列表 -->
    <div class="data-table">
      <h3>最近数据</h3>
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>数据类型</th>
            <th>处理状态</th>
            <th>更新时间</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in recentData" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.type }}</td>
            <td>
              <span :class="['status', item.status]">{{
                item.statusText
              }}</span>
            </td>
            <td>{{ item.updateTime }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const recentData = ref([
  {
    id: "001",
    type: "语音数据",
    status: "completed",
    statusText: "已完成",
    updateTime: "2024-03-20 10:30",
  },
  {
    id: "002",
    type: "文本数据",
    status: "processing",
    statusText: "处理中",
    updateTime: "2024-03-20 10:25",
  },
  {
    id: "003",
    type: "语音数据",
    status: "completed",
    statusText: "已完成",
    updateTime: "2024-03-20 10:20",
  },
  {
    id: "004",
    type: "文本数据",
    status: "pending",
    statusText: "待处理",
    updateTime: "2024-03-20 10:15",
  },
  {
    id: "005",
    type: "语音数据",
    status: "completed",
    statusText: "已完成",
    updateTime: "2024-03-20 10:10",
  },
]);
</script>

<style scoped>
.data-overview {
  padding: 2rem;
}

.page-title {
  color: #2c3e50;
  margin-bottom: 2rem;
}

.stats-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
  margin-bottom: 3rem;
}

.stat-card {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  text-align: center;
}

.stat-value {
  font-size: 2rem;
  font-weight: bold;
  color: #3498db;
  margin-bottom: 0.5rem;
}

.stat-label {
  color: #666;
  font-size: 0.9rem;
}

.data-table {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.data-table h3 {
  color: #2c3e50;
  margin-bottom: 1.5rem;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th,
td {
  padding: 1rem;
  text-align: left;
  border-bottom: 1px solid #eee;
}

th {
  font-weight: 600;
  color: #2c3e50;
}

.status {
  padding: 0.25rem 0.75rem;
  border-radius: 1rem;
  font-size: 0.85rem;
}

.status.completed {
  background-color: #e8f5e9;
  color: #2e7d32;
}

.status.processing {
  background-color: #e3f2fd;
  color: #1976d2;
}

.status.pending {
  background-color: #fff3e0;
  color: #f57c00;
}
</style>
