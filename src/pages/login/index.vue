<template>
  <div class="content">
    <img class="logo" src="@/static/img/denglu/logo.png" alt="" />
    <div class="logo-title">陕煤矿业</div>
    <div class="login-container">
      <div class="login-user flex flex">
        <div class="icon-container">
          <img src="@/static/img/denglu/icon.png" alt="" />
          <span>账号</span>
        </div>
        <div class="login-input">
          <input v-model="username" type="text" placeholder="请输入手机号" />
        </div>
      </div>
      <div class="login-password flex">
        <div class="icon-container flex">
          <img src="@/static/img/denglu/密码.png" alt="" />
          <span>密码</span>
        </div>
        <div class="login-input">
          <input v-model="password" type="password" placeholder="请输入密码" />
        </div>
      </div>
      <div class="next-btn" @click="handlerLogin">登录</div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      username: "",
      password: ""
    };
  },
  methods: {
    handlerLogin() {
      if (!this.username) {
        return uni.showToast({
          title: "请输入手机号",
          icon: "none"
        });
      }
      if (!this.password) {
        return uni.showToast({
          title: "请输入密码",
          icon: "none"
        });
      }
      uni.showToast({
        title: "登录成功",
        icon: "success"
      });
      setTimeout(() => {
        uni.navigateTo({
          url: "/pages/index/index"
        });
      }, 1200);
    }
  }
};
</script>

<style scoped lang="less">
.content {
  background: url("@/static/img/denglu/背景.png") no-repeat;
  background-size: 100% 100%;
  .logo {
    width: 170rpx;
    height: 170rpx;
    margin-top: 160rpx;
  }
  .logo-title {
    font-size: 48rpx;
    font-weight: 600;
    font-family: c2;
    letter-spacing: 1px;
    margin-top: 20rpx;
  }
  .login-container {
    margin: 116rpx auto 0;
    width: 560rpx;
  }
  .login-user,
  .login-password {
    height: 92rpx;
    border: 1px solid #ececec;
    border-radius: 46rpx;
  }
  .login-password {
    margin-top: 28rpx;
  }
  .login-container {
    font-size: 28rpx;
    img {
      width: 28rpx;
      margin-left: 50rpx;
      margin-right: 20rpx;
    }
  }
  .login-input {
    text-align: left;
    margin-left: 30rpx;
    flex: 1;
    input {
      font-size: 24rpx;
    }
  }
}
.next-btn {
  width: 100%;
  margin-top: 100rpx;
}
</style>
