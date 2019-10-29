<template>
  <div id="app">
    <el-container class="full">
      <el-header class="bg-primary">头部</el-header>
      <el-container>
        <el-aside width="200px" class="bg-light">
          <el-menu
      default-active="/"
      class="el-menu-vertical-demo"
      :router="true"
      >
       
      <el-menu-item index="/">
        <i class="el-icon-menu"></i>
        <span slot="title">首页</span>
      </el-menu-item>
      <el-menu-item index="/about" >
        <i class="el-icon-document"></i>
        <span slot="title">关于</span>
      </el-menu-item>
      
    </el-menu>
        </el-aside>
        <el-container>
          <el-main>
            <router-view></router-view>
          </el-main>
          <el-footer class="bg-dark">页脚</el-footer>
        </el-container>
      </el-container>
    </el-container>
  </div>
</template>
<style lang="less">
.full{
  position: absolute;
  left:0;
  right:0;
  top:0;
  bottom: 0;
}
.bg-primary{
  background-color: dodgerblue;
  color:#fff;
  }
.bg-light{
  background-color: #f0f0f0;
}
.bg-dark{
   background-color: #484848;
   color:#fff;
}
</style>
