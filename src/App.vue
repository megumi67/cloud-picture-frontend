<template>
  <div id="app">
    <!-- 为内部的 Ant Design Vue 组件设置中文文案 -->
    <a-config-provider :locale="zhCN">
      <!-- 页面基础布局，包含导航栏、路由内容和页脚 -->
      <BasicLayout />
    </a-config-provider>
  </div>
</template>

<script setup lang="ts">
// 引入页面基础布局组件
import BasicLayout from '@/layouts/BasicLayout.vue'
// 引入 Ant Design Vue 简体中文语言包
import zhCN from 'ant-design-vue/es/locale/zh_CN'
// 引入后端健康检查接口
import { healthUsingGet } from '@/api/mainController.ts'
// 引入管理登录用户信息的 Pinia Store 创建函数
import { userLoginUserStore } from '@/stores/userLoginUserStore.ts'
//日期、时间组件显示中文
import dayjs from 'dayjs'
import 'dayjs/locale/zh-cn'

dayjs.locale('zh-cn')



// 获取登录用户 Store 实例
const loginUserStore = userLoginUserStore()
// 获取当前登录用户信息（具体逻辑在 Store 中实现）
loginUserStore.fetchUserLoginUser()

// 调用健康检查接口，在控制台查看后端返回结果
healthUsingGet().then((res) => {
  console.log(res)
})
</script>

<style scoped>
/* 当前组件的局部样式 */
</style>
