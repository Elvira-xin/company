<template>
  <div class="userList">
    <el-form
      :model="dynamicValidateForm"
      v-for="(domain, index) in dynamicValidateForm.domains"
      :key="domain.key"
      ref="dynamicValidateForm"
      :label="'银行' + index"
      label-width="100px"
      class="demo-dynamic"
    >
      <!-- 添加银行卡输入框 -->
      <el-form-item
        prop="bank"
        label="银行"
        :rules="[
      { required: true, message: '请输入正确的银行', trigger: 'blur' },
      { type: 'bank', message: '请输入正确的银行', trigger: 'blur,change' }]"
      >
        <el-input v-model="dynamicValidateForm.bank"></el-input>
      </el-form-item>
      <!-- 添加持卡人信息 -->
      <el-form-item
        prop="cart"
        label="持卡人信息"
        :rules="[
      { required: true, message: '信息不匹配，请输入正确的持卡人信息', trigger: 'blur' },
      { type: 'cart', message: '信息不匹配，请输入正确的持卡人信息', trigger: 'blur,change' }]"
      >
        <el-input v-model="dynamicValidateForm.cart"></el-input>
      </el-form-item>
      <!-- 添加卡号 -->
      <el-form-item
        prop="cartnumber"
        label="银行卡号"
        :rules="[
      { required: true, message: '请输入正确的卡号', trigger: 'blur' },
      { type: 'cartnumber', message: '请输入正确的卡号', trigger: 'blur,change' }]"
      >
        <el-input v-model="dynamicValidateForm.cartnumber"></el-input>
      </el-form-item>

      <!-- <el-form-item
        v-for="(domain, index) in dynamicValidateForm.domains"
        :label="'域名' + index"
        :key="domain.key"
        :prop="'domains.' + index + '.value'"
        :rules="{
      required: true, message: '域名不能为空', trigger: 'blur'
    }"
      >-->
      <!-- <el-input v-model="domain.value"></el-input> -->
      <!-- </el-form-item> -->
      <div class="btns">
        <el-button type="primary" @click="submitForm('dynamicValidateForm')">提交</el-button>
        <el-button @click="addDomain">新增银行</el-button>
        <el-button @click="resetForm('dynamicValidateForm')">重置</el-button>
        <el-button @click="removeDomain(domain)">删除</el-button>
      </div>
    </el-form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      dynamicValidateForm: {
        domains: [
          {
            value: '',
            bank: '',
            cart: '',
            cartnumber: '',
            index: ''
          }
        ],
        bank: '',
        cart: '',
        cartnumber: ''
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
    },
    removeDomain (item) {
      console.log(item)
      var index = this.dynamicValidateForm.domains.indexOf(item)
      if (index !== -1) {
        this.dynamicValidateForm.domains.splice(index, 1)
      }
    },
    addDomain () {
      //   console.log(this.dynamicValidateForm.domains.index)
      this.dynamicValidateForm.domains.push({
        value: '',
        key: Date.now()
      })
    }
  }
}
</script>
<style lang="less" scoped>
.userList {
  width: 500px;
  height: 200px;
}
.btns {
  float: right;
}
</style>
