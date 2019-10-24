<template>
  <div class="home">
    <el-container>
      <div class="el-aside">
        <!-- 导航菜单--侧栏 -->
        <el-menu
          default-active="1-4-1"
          class="el-menu-vertical-demo"
          background-color="#eee"
          text-color="#000"
          :collapse="isCollapse"
        >
          <!-- 头像 -->
          <img
            src="http://nwzimg.wezhan.cn/contents/sitefiles2031/10157609/images/8574420.png"
            alt
            class="avatar"
          />
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">首页</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1"  @click="addTab(editableTabsValue2)">选项1</el-menu-item>
              <el-menu-item index="1-2-1">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">交易</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-2">选项1</el-menu-item>
              <el-menu-item index="1-2-2">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">财务</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-3">选项1</el-menu-item>
              <el-menu-item index="1-2-3">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">角色管理</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-4">选项1</el-menu-item>
              <el-menu-item index="1-2-4">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">导航一</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-5">选项1</el-menu-item>
              <el-menu-item index="1-2-5">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">导航一</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-6">选项1</el-menu-item>
              <el-menu-item index="1-2-6">选项2</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
        </el-menu>
      </div>
      <el-container>
        <el-header class="header">
          <span class="myicon myicon-menu toggle-btn" @click="isCollapse=!isCollapse"></span>
          <span class="welcome">欢迎进入摩富金服后台管理系统</span>
          <a href="javascript:;" class="exit">退出</a>
        </el-header>

        <!-- <div class="homeTab">

        </div> -->
        <el-mian class="homeTab">
             <el-tabs v-model="editableTabsValue2" type="card" closable @tab-remove="removeTab">
            <el-tab-pane
              v-for="(item) in editableTabs2"
              :key="item.name"
              :label="item.title"
              :name="item.name"
            >{{item.content}}</el-tab-pane>
          </el-tabs>
        </el-mian>
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
      editableTabs2: [
        {
          title: 'Tab 1',
          name: '1',
          content: 'Tab 1 content'
        },
        {
          title: 'Tab 2',
          name: '2',
          content: 'Tab 2 content'
        }
      ],
      tabIndex: 2
    }
  },
  methods: {
    addTab (targetName) {
      console.log(targetName)
      let newTabName = ++this.tabIndex + ''
      this.editableTabs2.push({
        title: 'New Tab',
        name: newTabName,
        content: 'New Tab content'
      })
      this.editableTabsValue2 = newTabName
    },
    removeTab (targetName) {
      let tabs = this.editableTabs2
      let activeName = this.editableTabsValue2
      if (activeName === targetName) {
        tabs.forEach((tab, index) => {
          if (tab.name === targetName) {
            let nextTab = tabs[index + 1] || tabs[index - 1]
            if (nextTab) {
              activeName = nextTab.name
            }
          }
        })
      }

      this.editableTabsValue2 = activeName
      this.editableTabs2 = tabs.filter(tab => tab.name !== targetName)
    }
  }
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
    width: 95%;
    height: 95%;
    box-sizing: border-box;
    text-align: center;
    box-shadow: 0 1px 5px #ccc;
    background-size: cover;
    overflow: hidden;
    display: flex;
    margin: 10px;
    // background-color: #db7e0c;
    // left: 25%;
  }
  .header {
    height: 120px;
    width: 100%;
    background-color: #eee;
    padding: 0 20px;
  }
  .homeTab{
    margin: 10px 0 0 10px;
    border-left: 0.5px solid #eee;
    width: 100%;
    height: 100%;
  }
  .toggle-btn {
    font-size: 30px;
    color: #545c64;
    line-height: 60px;
    float: left;
    cursor: pointer;
  }
  .welcome {
    color: #545c64;
    line-height: 60px;
    margin-left: 50px;
  }
  .exit {
    color: #545c64;
    float: right;
    line-height: 50px;
    &:hover {
      color: #4292cf;
    }
  }
}

.el-menu-vertical-demo:not(.el-menu--collapse) {
  // box-shadow: 50px 0px 20px red;
  border-right: 8px solid #eee;
  width: 200px;
  // min-height: 200px;
}
</style>
