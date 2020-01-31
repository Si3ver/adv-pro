<template>
  <div id="app">
    <a-button>按钮</a-button>
    <div id="nav">
      <router-link to="/dashboard/analysis">仪表盘</router-link>
      <router-link to="/form">表单</router-link>
    </div>
    <router-view></router-view>
  </div>
</template>

<style lang="less"></style>
