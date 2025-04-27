<template>
  <div class="analysis-report">
    <h2 class="page-title">分析报告</h2>

    <!-- 报告生成区域 -->
    <div class="report-generator">
      <div class="form-group">
        <label>选择数据类型</label>
        <select v-model="selectedDataType">
          <option value="voice">语音数据</option>
          <option value="text">文本数据</option>
          <option value="all">所有数据</option>
        </select>
      </div>

      <div class="form-group">
        <label>时间范围</label>
        <div class="date-range">
          <input type="date" v-model="startDate" />
          <span>至</span>
          <input type="date" v-model="endDate" />
        </div>
      </div>

      <button class="generate-btn" @click="generateReport">生成报告</button>
    </div>

    <!-- 报告列表 -->
    <div class="report-list">
      <h3>历史报告</h3>
      <div class="report-cards">
        <div v-for="report in reports" :key="report.id" class="report-card">
          <div class="report-info">
            <h4>{{ report.title }}</h4>
            <p class="report-meta">
              <span>{{ report.date }}</span>
              <span>{{ report.type }}</span>
            </p>
            <p class="report-desc">{{ report.description }}</p>
          </div>
          <div class="report-actions">
            <button class="action-btn view">查看</button>
            <button class="action-btn download">下载</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const selectedDataType = ref("all");
const startDate = ref("");
const endDate = ref("");

const reports = ref([
  {
    id: 1,
    title: "语音识别准确率分析报告",
    date: "2024-03-20",
    type: "语音数据",
    description:
      "本报告分析了过去一周的语音识别准确率数据，包含详细的错误分析和改进建议。",
  },
  {
    id: 2,
    title: "文本处理效率报告",
    date: "2024-03-19",
    type: "文本数据",
    description: "分析了文本处理pipeline的性能指标，识别了潜在的性能瓶颈。",
  },
  {
    id: 3,
    title: "综合性能评估报告",
    date: "2024-03-18",
    type: "所有数据",
    description:
      "对系统整体性能进行了全面评估，包括准确率、处理速度等多个维度。",
  },
]);

const generateReport = () => {
  // TODO: 实现报告生成逻辑
  console.log("生成报告", {
    type: selectedDataType.value,
    startDate: startDate.value,
    endDate: endDate.value,
  });
};
</script>

<style scoped>
.analysis-report {
  padding: 2rem;
}

.page-title {
  color: #2c3e50;
  margin-bottom: 2rem;
}

.report-generator {
  background: white;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  margin-bottom: 2rem;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  color: #2c3e50;
  font-weight: 500;
}

select,
input {
  width: 100%;
  padding: 0.5rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
}

.date-range {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.date-range input {
  width: calc(50% - 1rem);
}

.generate-btn {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s;
}

.generate-btn:hover {
  background-color: #2980b9;
}

.report-list {
  background: white;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.report-list h3 {
  color: #2c3e50;
  margin-bottom: 1.5rem;
}

.report-cards {
  display: grid;
  gap: 1.5rem;
}

.report-card {
  border: 1px solid #eee;
  border-radius: 8px;
  padding: 1.5rem;
  display: flex;
  justify-content: space-between;
  align-items: start;
}

.report-info {
  flex: 1;
}

.report-info h4 {
  color: #2c3e50;
  margin: 0 0 0.5rem 0;
}

.report-meta {
  color: #666;
  font-size: 0.9rem;
  margin-bottom: 0.5rem;
}

.report-meta span:not(:last-child)::after {
  content: "•";
  margin: 0 0.5rem;
}

.report-desc {
  color: #666;
  font-size: 0.9rem;
  margin: 0;
}

.report-actions {
  display: flex;
  gap: 0.5rem;
}

.action-btn {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 0.9rem;
  transition: background-color 0.3s;
}

.action-btn.view {
  background-color: #e3f2fd;
  color: #1976d2;
}

.action-btn.download {
  background-color: #e8f5e9;
  color: #2e7d32;
}

.action-btn:hover {
  opacity: 0.8;
}
</style>
