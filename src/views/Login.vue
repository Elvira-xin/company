<template>
  <div class="login">
    <!-- 登录框 -->
    <div class="loginForm">
      <div class="loginForm-top">
        后台管理系统
        <span class="bg1"></span>
        <span class="bg2"></span>
      </div>
      <el-form
        :model="ruleForm"
        :rules="rules"
        ref="ruleForm"

        class="demo-ruleForm"
      >
        <!-- 输入框 -->
<<<<<<< HEAD
        <el-form-item prop="username">
          <el-input v-model="ruleForm.username" placeholder="请输入账号" prefix-icon="myicon-user" class="loginForm-input"></el-input>
        </el-form-item>
        <el-form-item  prop="password">
          <el-input v-model="ruleForm.password" placeholder="请输入密码" prefix-icon="myicon-key" class="loginForm-input"></el-input>
=======

        <el-form-item label="用户名" prop="username">
          <el-input v-model="ruleForm.username" placeholder="用户名" prefix-icon="myicon-user"></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="password">
          <el-input v-model="ruleForm.password" placeholder="密码" prefix-icon="myicon-key"></el-input>
>>>>>>> 1e050fcc586ea3c4bdfaa1e71b8cf06c5d10fd57
        </el-form-item>
        <el-form-item>
          <el-button class="login-btn" type="warning" plain @click="submitForm('ruleForm')">立即登录</el-button>
        </el-form-item>
      </el-form>
       <el-checkbox v-model="checked" class="login-auto">两周内自动登录</el-checkbox>
      <span class="findPassword">
        <a href="#">忘记密码？</a>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      ruleForm: {
        username: '',
        password: ''
      },
      rules: {
        username: [
          { required: true, message: '请输入正确的用户名', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入正确的密码', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    submitForm () {}
  }
}
</script>

<style lang="less" scoped>
.login {
  position: fixed;
  width: 100%;
<<<<<<< HEAD
  height: 90%;
    top: 5%;
=======
  height: 100%;
>>>>>>> 1e050fcc586ea3c4bdfaa1e71b8cf06c5d10fd57
  background-color: #2f4050;
  background: url("../img/308296275.jpg") no-repeat;
  background-size: cover;
  .loginForm {
    position: absolute;
    left: 0;
    right: 0;
<<<<<<< HEAD
    bottom: -48px;
    width: 408px;
    height: 428px;
    margin: 200px auto;
    background: white;
    border-radius: 12px;
    .loginForm-top {
      border-radius: 12px 12px 0 0;
=======
    bottom: 90px;
    width: 400px;
    height: 300px;
    margin: 200px auto;
    padding: 30px;
    background: #fbfeff;
    opacity: 0.9;
    border: 7px solid #eee;
    // border-radius: 30px;
    .loginForm-tab {
>>>>>>> 1e050fcc586ea3c4bdfaa1e71b8cf06c5d10fd57
      width: 100%;
      height: 87px;
      background-color: #db7e0c;
      opacity: .85;
      //   color: #bd3633;
      color: #fff;
      font-size:34px;
      font-weight: 400;
      line-height: 87px;
      text-align: center;
      margin-bottom: 25px;
      position: relative;
      .bg1 {
        background-color: #eee;
        top: -38px;
        right: -16px;
        opacity: 0.1;
        position: absolute;
        display: inline-block;
        width: 94px;
        height: 94px;
        border-radius: 50%;
      }
      .bg2 {
        background-color: #eee;
        width: 94px;
        height: 94px;
        position: absolute;
        opacity: 0.1;
        border-radius: 50%;
        top:35px;
        left: -22px;
      }
    }
    .demo-ruleForm {
<<<<<<< HEAD
      padding: 20px 40px 15px 30px;
    }
    /deep/ .loginForm-input .el-input__inner {
        border: 0 none;
        border-bottom: 1px solid #ccc;
        border-radius: 0px;

=======
      padding: 0px 40px 20px 30px;
>>>>>>> 1e050fcc586ea3c4bdfaa1e71b8cf06c5d10fd57
    }
    .login-btn {
      width: 100%;
    border-radius: 16px;
    }
    .login-auto{
        position: absolute;
        bottom: 70px;
        left: 60px;
        color: #9abcda;
    }
    .findPassword {
      position: absolute;
      right: 60px;
      bottom: 73px;
      a {
        color: #4b6796;
        font-size: 12px;
      }
    }
  }
}
</style>
