<template>
  <div class="visualization">
    <h2 class="page-title">可视化图表</h2>

    <!-- 图表类型选择 -->
    <div class="chart-controls">
      <div class="control-group">
        <label>选择图表类型</label>
        <select v-model="selectedChartType">
          <option value="line">折线图</option>
          <option value="bar">柱状图</option>
          <option value="pie">饼图</option>
          <option value="scatter">散点图</option>
        </select>
      </div>

      <div class="control-group">
        <label>数据范围</label>
        <select v-model="dataRange">
          <option value="day">今日</option>
          <option value="week">本周</option>
          <option value="month">本月</option>
          <option value="year">全年</option>
        </select>
      </div>

      <button class="refresh-btn" @click="refreshData">刷新数据</button>
    </div>

    <!-- 图表展示区域 -->
    <div class="charts-container">
      <div class="chart-wrapper">
        <h3>准确率趋势</h3>
        <div class="chart" ref="accuracyChart"></div>
      </div>

      <div class="chart-wrapper">
        <h3>数据分布</h3>
        <div class="chart" ref="distributionChart"></div>
      </div>

      <div class="chart-wrapper">
        <h3>处理速度分析</h3>
        <div class="chart" ref="speedChart"></div>
      </div>

      <div class="chart-wrapper">
        <h3>错误类型统计</h3>
        <div class="chart" ref="errorChart"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import * as echarts from "echarts";

const selectedChartType = ref("line");
const dataRange = ref("week");

// 图表引用
const accuracyChart = ref(null);
const distributionChart = ref(null);
const speedChart = ref(null);
const errorChart = ref(null);

// 初始化图表
const initCharts = () => {
  // 准确率趋势图
  const accuracy = echarts.init(accuracyChart.value);
  accuracy.setOption({
    title: { text: "准确率趋势" },
    tooltip: { trigger: "axis" },
    xAxis: {
      type: "category",
      data: ["周一", "周二", "周三", "周四", "周五", "周六", "周日"],
    },
    yAxis: { type: "value", min: 80 },
    series: [
      {
        data: [93, 92, 95, 89, 94, 96, 95],
        type: "line",
        smooth: true,
      },
    ],
  });

  // 数据分布图
  const distribution = echarts.init(distributionChart.value);
  distribution.setOption({
    title: { text: "数据类型分布" },
    tooltip: { trigger: "item" },
    series: [
      {
        type: "pie",
        radius: "60%",
        data: [
          { value: 1048, name: "语音数据" },
          { value: 735, name: "文本数据" },
          { value: 580, name: "图像数据" },
          { value: 484, name: "视频数据" },
        ],
      },
    ],
  });

  // 处理速度图
  const speed = echarts.init(speedChart.value);
  speed.setOption({
    title: { text: "处理速度" },
    tooltip: { trigger: "axis" },
    xAxis: { type: "category", data: ["语音", "文本", "图像", "视频"] },
    yAxis: { type: "value" },
    series: [
      {
        data: [120, 200, 150, 80],
        type: "bar",
      },
    ],
  });

  // 错误类型图
  const error = echarts.init(errorChart.value);
  error.setOption({
    title: { text: "错误类型分布" },
    tooltip: { trigger: "item" },
    series: [
      {
        type: "pie",
        radius: ["40%", "70%"],
        data: [
          { value: 335, name: "识别错误" },
          { value: 310, name: "格式错误" },
          { value: 234, name: "超时" },
          { value: 135, name: "其他" },
        ],
      },
    ],
  });

  // 监听窗口大小变化
  window.addEventListener("resize", () => {
    accuracy.resize();
    distribution.resize();
    speed.resize();
    error.resize();
  });
};

// 刷新数据
const refreshData = () => {
  // TODO: 实现数据刷新逻辑
  console.log("刷新数据", {
    chartType: selectedChartType.value,
    range: dataRange.value,
  });
};

onMounted(() => {
  initCharts();
});
</script>

<style scoped>
.visualization {
  padding: 2rem;
}

.page-title {
  color: #2c3e50;
  margin-bottom: 2rem;
}

.chart-controls {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  margin-bottom: 2rem;
  display: flex;
  gap: 2rem;
  align-items: flex-end;
}

.control-group {
  flex: 1;
}

.control-group label {
  display: block;
  margin-bottom: 0.5rem;
  color: #2c3e50;
  font-weight: 500;
}

select {
  width: 100%;
  padding: 0.5rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
}

.refresh-btn {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 0.5rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s;
}

.refresh-btn:hover {
  background-color: #2980b9;
}

.charts-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
}

.chart-wrapper {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.chart-wrapper h3 {
  color: #2c3e50;
  margin-bottom: 1rem;
}

.chart {
  height: 300px;
  width: 100%;
}
</style>
