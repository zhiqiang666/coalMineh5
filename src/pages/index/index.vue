<template>
  <view class="content">
    <img
      src="@/static/img/首页/logo.png"
      style="
        width: 200rpx;
        height: 200rpx;
        margin-top: 100rpx;
        margin-bottom: 40rpx;
      "
      alt=""
    />
    <view>
      <span style="font-size: 36rpx">驾驶员身份信息登记</span>
    </view>
    <view
      class="flex"
      style="margin: 0 auto; width: 600rpx; height: 380rpx; margin-top: 40rpx"
    >
      <view
        style="width: 50%; height: 100%"
        class="info"
        @click="pageTo('/pages/index/guide')"
      >
        <text class="info-label">信息登记</text>
      </view>
      <view style="width: 50%; margin-left: 6rpx; height: 100%">
        <div style="padding-bottom: 6rpx; box-sizing: border-box; height: 50%">
          <view
            class="search"
            style="height: 100%"
            @click="pageTo('/pages/search/index')"
          >
            <text class="search-label">查询</text></view
          >
        </div>
        <div style="padding-top: 6rpx; box-sizing: border-box; height: 50%">
          <view
            class="login"
            style="height: 100%"
            @click="pageTo('/pages/login/index')"
          >
            <text class="search-label">登陆</text>
          </view>
        </div>
      </view>
    </view>
    <view class="tip-container">
      <view class="tip">温馨提示：</view>
      <view class="tip-content"
        >在信息登记前，请提前打开交管12123AFP应用，在应用首页选择＜驾驶证电子版>打开后进行截图，以便于在登记时进行上传审校！</view
      >
    </view>
    <view class="footer-label"> 陕西陕媒黄陵矿业有限公司一号煤矿 </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      title: "Hello"
    };
  },
  onLoad() {},
  methods: {
    pageTo(url) {
      uni.navigateTo({
        url: url
      });
    }
  }
};
</script>

<style scoped lang="less">
.content {
  background: url("@/static/img/首页/背景.png") no-repeat;
  background-size: 100% 100%;
}

.search {
  box-sizing: border-box;
  padding-bottom: 6rpx;
}
.login {
  box-sizing: border-box;
  padding-top: 6rpx;
}
.info {
  margin-right: 6rpx;
}
.search {
  background: url("@/static/img/首页/查询.png") no-repeat;
  background-size: 100% 100%;
}
.info {
  background: url("@/static/img/首页/信息登记.png") no-repeat;
  background-size: 100% 100%;
  padding-bottom: 12rpx;
  box-sizing: border-box;
}
.login {
  // margin-top: 12rpx;
  background: url("@/static/img/首页/登录.png") no-repeat;
  background-size: 100% 100%;
}
.info-label,
.search-label {
  color: white;
  letter-spacing: 2px;
  font-family: c2;
}
.info-label {
  display: inline-block;
  margin-top: 230rpx;
  font-size: 30rpx;
}
.search-label {
  display: flex;
  height: 100%;
  align-items: center;
  margin-left: 160rpx;
}
.tip-container {
  text-align: left;
  width: 600rpx;
  margin: 0 auto;
}
.tip {
  font-size: 28rpx;
  margin-top: 20rpx;
  margin-bottom: 12rpx;
}
.tip-content {
  font-size: 24rpx;
  color: #666;
  letter-spacing: 1px;
}
.footer-label {
  font-size: 24rpx;
  position: absolute;
  bottom: 2px;
  width: 100%;
  text-align: center;
  color: #666;
}
</style>
