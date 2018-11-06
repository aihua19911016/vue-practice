<template>
  <div>
    <div style="display: block">
      <span>用户名</span>
      <input v-model="name"/>
    </div>
    <div style="display: block">
      <span>密码</span>
      <input type="password" v-model="password"/>
    </div>
    <input type="submit" value="登录" @click="login()"/>
    <input type="submit" value="页面跳转" @click="skip()"/>


  </div>
</template>
<script>
  export default {
    data() {
      return {
        name: '',//用户名
        password: ''//密码
      }
    },
    methods: {
      login() {//登录
        alert('用户名：' + this.name + '  密码：' + this.password)
      },
      skip() {//页面跳转
        this.$router.push({path: '/home'})
//        this.$router.replace({path: '/home'})
      }
    }
  }

</script>
<style>

</style>
