<template>
  <div class="logintext">
    <h1>登录</h1>
  <el-row type="flex" justify="center">
    <el-form ref="loginForm" :model="user" :rules="rules" status-icon label-width="80px">
      <el-form-item label="邮箱" prop="mail">
        <el-input v-model="user.mail"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="pwd">
        <el-input v-model="user.pwd" type="password"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button  @click="login">登录</el-button>
      </el-form-item>
    </el-form>
  </el-row>
  </div>
</template>

<script>
  import axios from 'axios'
  import qs from 'qs'
  export default {
    data() {
      return {
        user: {},
        rules: {
          mail: [
            {required: true, message: '邮箱不能为空', trigger: 'blur'}
          ],
          pwd: [
            {required: true, message: '密码不能为空', trigger: 'blur'}
          ]
        }
      }
    },
    methods: {
      login() {
          this.$refs.loginForm.validate((valid) => {
            if (valid) {
              this.$axios.post(
                'http://localhost:8080/online_answer/user/login',
                qs.stringify({
                  // loginForm: this.loginForm
                  mail:"246228924@qq.com",
                  pwd:"1"
                })
              ).then(response => {
                console.log(response)
                console.log("登录成功")
                const {data} = response
                console.log('data',data)
                this.data = data
              }).catch(error => {
                console.log(error)
              })
            } else {
              return false
            }
          })
      }
    }
  }
</script>

<style>
  .el-button{
    background-color: lightcoral;
    color: white;
  }
  .logintext{
    text-align:center;
  }
</style>
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
