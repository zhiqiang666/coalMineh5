<template>
  <div class="content">
    <img class="logo" src="@/static/img/登录/logo.png" alt="" />
    <div class="logo-title">陕煤矿业</div>
    <div class="login-container">
      <div class="login-user flex ">
        <div class="icon-container">
          <img src="@/static/img/登录/icon.png" alt="" />
          <span>身份证号</span>
        </div>
        <div class="login-input">
          <input v-model="username" type="text" placeholder="请输入身份证号" />
        </div>
      </div>
      <div class="next-btn" @click="handlerLogin">查询</div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      username: "",
    };
  },
  methods: {
    handlerLogin() {
      if (!this.username) {
        return uni.showToast({
          title: "请输入身份证号",
          icon: "none"
        });
      }
      uni.showToast({
        title: "登记成功",
        icon: "success"
      });
      setTimeout(() => {
        uni.navigateTo({
          url: "/pages/search/page"
        });
      }, 1200);
    }
  }
};
</script>

<style scoped lang="less">
.content {
  background: url("@/static/img/登录/背景.png") no-repeat;
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
    border-bottom: 1px solid #b2b2b2;
  }
  .login-password {
    margin-top: 28rpx;
  }
  .login-container {
    font-size: 28rpx;
    img {
      width: 28rpx;
      margin-right: 20rpx;
    }
  }
  .login-input {
    text-align: right;
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
  width: 400rpx;
}
</style>
