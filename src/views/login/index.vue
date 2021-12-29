<template>
  <div class="login-container">
    <el-form class="login_form" ref="form" :model="user" >
  <el-form-item >
    <el-input v-model="user.mobile"
              placeholder="请输入用户名"
    ></el-input>
  </el-form-item>
  <el-form-item >
    <el-input v-model="user.code"
              placeholder="请输入密码"
    ></el-input>
  </el-form-item>
  <el-form-item >
    <el-checkbox v-model="checked">我已经阅读并同意用户协议和隐私条款</el-checkbox>
  </el-form-item>
  <el-form-item>
    <el-button class="login_btn" :loading="loginLoading" type="primary" @click="onLogin">登录</el-button>
  </el-form-item>
    </el-form>
  </div>
</template>

<script>
import request from '@/utils/request'
export default {
  name: 'LoginIndex',
  components: {},
  props: {},
  data () {
    return {
      user: {
        mobile: '',
        code: ''
      },
      checked: false,
      loginLoading: false
    }
  },
  computed: {},
  watch: {},
  created () {

  },
  mounted () {},
  methods: {
    onLogin () {
      this.loginLoading = true
      //  const user = this.user
      request({
        method: 'GET',
        url: 'https://api.apiopen.top/getJoke?page=1&count=2&type=video'
        //  url: 'http://ttapi.research.itcast.cn/mp/v1_0/authorizations',
        //  data: user
      }).then(res => {
        this.loginLoading = false
        console.log(res)
        if (res.data.code === 200) {
          console.log(1111)
        }
      }).catch(err => {
        console.log('登录失败', err)
        this.$message.error({
          message: '用户名或者密码错误',
          center: true
        })
        this.loginLoading = false
      })
    }
  }
}
</script>

<style scoped lang="less">
  .login-container {
    //   font-size: 200px;
    //   color: antiquewhite;
    //   width: 500px;
    //   height: 400px;
    //   background-color: antiquewhite;
    //   transform: translate(-50%,-50%);
    //   position: absolute;
    //   top: 50%;
    //   left: 50%;
    position: fixed;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    .login_form{
        background-color: #fff;
        padding: 50px;
        min-width: 300px;
        border-radius: 5px;
    }
    .login_btn {
        width: 100%;
    }
  }
</style>
