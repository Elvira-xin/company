<template>
  <div class="home">
    <el-container>
      <div class="menu-aside">
        <!-- 导航菜单--侧栏 -->
        <el-menu
          default-active="1-4-1"
          background-color="#3a4651"
          text-color="#9ca2a8"
          :collapse="isCollapse"
        >
          <!-- logo部分开始 -->
          <img
            src="http://nwzimg.wezhan.cn/contents/sitefiles2031/10157609/images/8574420.png"
            alt
            class="avatar"
          />
          <!-- logo部分结束 -->

          <!-- 左侧菜单项开始 -->
          <el-submenu :index="first.id+''" v-for="first in menuList" :key="first.id">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title">{{first.name}}</span>
            </template>

            <!-- 二级菜单项开始 -->
            <el-menu-item
              :index="second.id+''"
              v-for="second in first.children"
              :key="second.id"
              @click="addTab(editableTabsValue2)"
            >
              <template slot="title">
                <i class="el-icon-location-outline"></i>
                <span slot="title">{{second.name}}</span>
              </template>
            </el-menu-item>
            <!-- 二级菜单项结束 -->
          </el-submenu>
          <!-- <el-menu-item index="/home/index" @click="addTab(editableTabsValue2)">选项1</el-menu-item> -->
          <!-- 左侧菜单项结束 -->
        </el-menu>
      </div>
      <el-container>
        <!-- 右侧顶部开始 -->
        <el-header class="header">
          <span class="myicon myicon-menu toggle-btn" @click="isCollapse=!isCollapse"></span>
          <span class="welcome">欢迎进入摩富金服后台管理系统</span>
          <a href="javascript:;" class="exit">安全退出</a>
        </el-header>
        <!-- 右侧顶部结束 -->

        <!-- 右侧标签页开始 -->
        <div class="homeTab">
          <el-mian>
            <el-tabs v-model="editableTabsValue2" type="card" closable @tab-remove="removeTab">
              <el-tab-pane
                v-for="(item) in editableTabs2"
                :key="item.name"
                :label="item.title"
                :name="item.name"
              ></el-tab-pane>
            </el-tabs>
            <!-- <router-view></router-view> -->
            <UserList></UserList>
          </el-mian>
          <!-- 右侧标签页结束 -->
        </div>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import UserList from '../components/users/userList'
export default {
  components: {
    UserList
  },
  data () {
    return {
      menuList: [
        {
          id: 1,
          name: '用户管理',
          children: [
            {
              id: 1 - 1,
              name: '用户列表'
            },
            {
              id: 1 - 2,
              name: '用户删除'
            },
            {
              id: 1 - 3,
              name: '用户管理'
            }
          ]
        },
        {
          id: 2,
          name: '文章管理'
        },
        {
          id: 3,
          name: '订单管理'
        },
        {
          id: 4,
          name: '管理员权限'
        },
        {
          id: 5,
          name: '系统统计'
        }
      ],
      isCollapse: false,
      editableTabsValue2: '',
      editableTabs2: [
        // {
        //   title: 'Tab 1',
        //   name: '1',
        //   content: 'Tab 1 content'
        // },
        // {
        //   title: 'Tab 2',
        //   name: '2',
        //   content: 'Tab 2 content'
        // }
      ],
      addtableTab: [
        {
          title: '用户权限列表',
          name: '3',
          content: '这是用户列表权限页'
        }
      ],
      tabIndex: ''
    }
  },
  methods: {
    addTab (targetName) {
      console.log(targetName)
      let newTabName = ++this.tabIndex + ''
      this.editableTabs2.push({
        title: 'New Tab',
        name: newTabName
        // content: 'New Tab content'
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
  .el-menu {
    width: auto;
  }
  // 如果是展开状态,那么宽度就是200px,如果是合并状态,宽度:auto
  .el-menu:not(.el-menu--collapse) {
    width: 200px;
    min-height: 400px;
  }
  .el-container {
    height: 100%;
  }
  .avatar {
    position: relative;
    width: 95%;
    height: 95%;
    box-sizing: border-box;
    text-align: center;
    // box-shadow: 1px 0px 3px  #ccc;
    background-size: cover;
    overflow: hidden;
    display: flex;
    padding: 8px;
    margin: 5px;
    // background-color: #db7e0c;
    // left: 25%;
  }
  .menu-aside {
    height: 1000px;
    width: 200px;
    // position: absolute;
    background-color: #3a4651;
    // overflow: auto;
    // border-right: 3px solid #3a4651;
    // display: block;
  }
  .header {
    height: 120px;
    width: 100%;
    background-color: #eee;
    padding: 0 20px;
  }
  .homeTab {
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
    // margin-left: 50px
    text-align: center;
    margin: auto;
    display: block;
  }
  .exit {
    color: #545c64;
    position: absolute;
    display: inline-block;
    // float: right;
    top: 20px;
    right: 25px;
    // line-height: 50px;
    &:hover {
      color: #4292cf;
    }
  }
}

// .el-menu-vertical-demo:not(.el-menu--collapse) {
//   // box-shadow: 50px 0px 20px red;
//   // border-right: 8px solid #eee;
//   width: 120px;
// }
</style>
