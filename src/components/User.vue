<template>
<div class="message">
  <mt-header fixed title="消 息"></mt-header>
  <div class="login" v-if="!isLogin">
    <mt-button class="btn-success" @click="showLoginFormHandle">登录</mt-button>
    <mt-button class="btn-warning" @click="showRegisterFormHandle">注册</mt-button>
  </div>
  <div class="content" v-if="isLogin">
    <mt-cell @click.native="redirectHandle()" title="投稿互动"></mt-cell>
    <mt-cell @click.native="redirectHandle('/user/funs')" title="我的投稿"></mt-cell>
    <mt-button type="danger" @click="logoutHandle">退出登录</mt-button>
  </div>
</div>
</template>

<script>
export default {
  name: 'User',
  props: ['isLogin'],
  data () {
    return {
    }
  },
  methods: {
    showLoginFormHandle () {
      this.$emit('showLoginForm')
    },
    showRegisterFormHandle () {
      this.$emit('showRegisterForm')
    },
    logoutHandle () {
      this.$emit('logout')
    },
    redirectHandle (path) {
      this.$router.push({path})
    }
  }
}
</script>

<style lang="sass" scoped>
.message
  .login
    padding: 1em
  button
    margin-top: 1em
    width: 100%
  .content
    padding: 1em
  .mint-cell
    margin-bottom: .25rem;
    border-radius: .25rem;
</style>
