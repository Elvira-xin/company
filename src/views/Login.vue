<template>
  <div class="login">
    <!-- 登录框 -->
    <div class="container">
      <!-- tab栏 -->
      <div class="loginForm-tab">
        <span class="login-account">摩富金服后台管理系统</span>
      </div>
      <el-form
        :model="ruleForm"
        :rules="rules"
        ref="ruleForm"
        label-width="70px"
        class="demo-ruleForm"
      >
        <!-- 输入框 -->

        <el-form-item label="用户名" prop="username">
          <el-input v-model="ruleForm.username" prefix-icon="myicon-user"></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="password">
          <el-input v-model="ruleForm.password" prefix-icon="myicon-key"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button class="login-btn" type="primary" plain @click="submitForm('ruleForm')">登录</el-button>
        </el-form-item>
      </el-form>
      <span class="findPassword">
        <a href="#">找回密码</a>
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
    submitForm (formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert('submit!')
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    resetForm (formName) {
      this.$refs[formName].resetFields()
    }
  }
}
</script>

 <style lang="less" scoped>
.login {
  position: fixed;
  width: 2000px;
  height: 1000px;
  background-color: #2f4050;
  background: url("../img/311993150.jpg") no-repeat;
  background-size: cover;
  .container {
    position: absolute;
    left: 0;
    right: 0;
    bottom: 182px;
    width: 420px;
    height: 300px;
    margin: 200px auto;
    padding: 30px;
    background: white;
    border: 7px solid #eee;
    border-radius: 30px;
    .loginForm-tab {
      width: 100%;
      line-height: 70px;
      text-align: center;
      font-size: 24px;
      margin-bottom: 25px;
      .login-account {
        color: #4b6796;
      }
    }
    .demo-ruleForm {
      padding: 0px 40px 15px 30px;
    }
    .login-btn {
      width: 100%;
    }
    .findPassword {
      position: absolute;
      right: 60px;
      bottom: 20px;
      a {
        color: #4b6796;
        font-size: 12px;
      }
    }
  }
}
</style>
