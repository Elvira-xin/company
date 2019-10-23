<template>
  <div class="home">
    <el-container>
      <div class="el-aside">
        <!-- 导航菜单--侧栏 -->
        <el-menu
          default-active="1-4-1"
          class="el-menu-vertical-demo"
          background-color="#545c64"
          text-color="#fff"
          :collapse="isCollapse"
        >
          <!-- 头像 -->
          <img src="../img/管理员.jpg" alt class="avatar" />
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">首页</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">交易</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">财务</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">角色管理</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">导航一</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">导航一</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
        </el-menu>
      </div>
      <el-container>
        <el-header class="header">
          <span class="myicon myicon-menu toggle-btn" @click="isCollapse=!isCollapse"></span>
          <!-- <span class="welcome">欢迎进入摩富金服后台管理系统</span> -->
          <a href="javascript:;" class="exit">退出</a>
        </el-header>

        <el-tabs v-model="editableTabsValue2" type="card" closable @tab-remove="removeTab">
          <el-tab-pane
            v-for="(item) in editableTabs2"
            :key="item.name"
            :label="item.title"
            :name="item.name"
          >{{item.content}}</el-tab-pane>
        </el-tabs>
        <el-mian></el-mian>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  data () {
    return {
      isCollapse: false,
      editableTabsValue2: '2',
      editableTabs2: [{
        title: 'Tab 1',
        name: '1',
        content: 'Tab 1 content'
      }, {
        title: 'Tab 2',
        name: '2',
        content: 'Tab 2 content'
      }],
      tabIndex: 2
    }
  },
  methods: {}
}
</script>

<style lang="less" scoped>
.home {
  height: 100%;
  el-menu {
    width: auto;
  }
  .avatar {
    position: relative;
    width: 90px;
    height: 90px;
    box-sizing: border-box;
    text-align: center;
    border-radius: 50%;
    border: 8px solid #fff;
    box-shadow: 0 1px 5px #ccc;
    background-size: cover;
    overflow: hidden;
    display: flex;
    margin: 15px 0;
    left: 25%;
  }
  .header {
    height: 120px;
    width: 100%;
    background-color: #545c64;
    padding: 0 20px;
  }
  .toggle-btn {
    font-size: 30px;
    color: #fff;
    line-height: 60px;
    float: left;
    cursor: pointer;
  }
  .welcome {
    color: #fff;
    line-height: 60px;
    margin-left: 50px;
  }
  .exit {
    color: #fff;
    float: right;
    line-height: 50px;
    &:hover {
      color: #4292cf;
    }
  }
}

.el-menu-vertical-demo:not(.el-menu--collapse) {
  width: 200px;
  min-height: 400px;
}
</style>
