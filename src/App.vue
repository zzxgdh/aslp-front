<script setup>
import { RouterView } from "vue-router";

import zhCn from "element-plus/es/locale/lang/zh-cn";
import { reactive } from "vue";

// const appStore = useAppStore()
// appStore.initThemeColor()

const font = reactive({
  color: "rgba(0, 0, 0, .15)",
});

const locale = zhCn;
</script>

<template>
  <RouterView />
</template>

<style>
#app {
  font-family: Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
