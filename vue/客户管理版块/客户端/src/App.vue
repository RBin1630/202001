<template>
  <div id="app">
    <!-- 抽屉（左侧导航） -->
    <div class="menu">
      <el-button type="primary" icon="el-icon-setting" circle @click="handleDrawer"></el-button>

      <el-drawer
        direction="ltr"
        :modal="false"
        :show-close="false"
        :visible.sync="drawerVisible"
        :withHeader="false"
      >
        <el-link type="info" @click="returnBack">返回</el-link>

        <el-menu :router="true" default-active="/">
          <el-menu-item index="/">
            <i class="el-icon-document"></i>
            <span slot="title">客户列表</span>
          </el-menu-item>
          <el-menu-item index="/create">
            <i class="el-icon-circle-plus-outline"></i>
            <span slot="title">新增客户</span>
          </el-menu-item>
          <el-menu-item index="/upload">
            <i class="el-icon-upload"></i>
            <span slot="title">批量上传</span>
          </el-menu-item>
        </el-menu>
      </el-drawer>
    </div>

    <!-- 视图容器 -->
    <keep-alive include="CustomList">
      <router-view></router-view>
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      drawerVisible: false
    };
  },
  methods: {
    handleDrawer() {
      this.drawerVisible = !this.drawerVisible;
    },
    returnBack() {
      this.$router.go(-1);
    }
  }
};
</script>

<style lang="less">
html,
body,
#app {
  height: 100%;
  overflow: hidden;
}

.menu {
  .el-menu {
    border-right: none !important;
  }

  .el-drawer {
    width: 180px !important;
  }

  .el-button {
    font-size: 24px !important;
    width: 40px !important;
    height: 40px !important;
    padding: 0 !important;

    position: fixed;
    top: 10px;
    left: 10px;
    z-index: 100;
  }

  .el-link {
    padding: 0 20px;
    line-height: 40px !important;
  }
}
</style>
