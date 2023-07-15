<template>
  <div class="content">
    <div class="container">
      <div class="warning-title">注意事项</div>
      <div class="warning-read">填写前请仔细阅读注意事项</div>
      <div class="process-container"></div>
      <div class="warning-info">
        <div class="warning-info-title">注意事项</div>
        <div class="warning-info-content">
          各位驾驶员在进行身份登记前，请提前打开
          [交管12123]APP，在首页点击[驾驶证电子版]选项，打开后截图保存至手机。如没有
        </div>
        <div class="prepare">进行身份登记时，应提前准备</div>
        <div class="process-info">
          <div>
            1.白底正面半身照，半身照头部标准与照片整体大小应符合正常比例。
          </div>
          <div>2.身份证照片(正面)</div>
          <div>3.电子驾照截图(通过交管12123APP申领)</div>
        </div>
      </div>
      <div class="next-btn" @click="pageTo">我已知晓，下一步</div>
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    pageTo() {
      uni.navigateTo({
        url: "/pages/register/index"
      });
    }
  }
};
</script>

<style scoped lang="less">
.content {
  background: url("@/static/img/注意事项/头图.png") no-repeat;
  background-size: 100%;
}
.container {
  width: 88%;
  height: 100%;
  margin: 0 auto;
  text-align: left;
  .warning-title {
    color: white;
    font-size: 60rpx;
    margin-left: 20rpx;
    padding-top: 50rpx;
  }
  .warning-read {
    display: inline-block;
    color: white;
    margin-left: 20rpx;
    background: url("@/static/img/注意事项/样式.png") no-repeat;
    background-size: 100% 100%;
    font-size: 24rpx;
    padding: 8rpx 16rpx;
    margin-top: 26rpx;
  }
  .process-container {
    margin-top: 80rpx;
    width: 100%;
    height: 170rpx;
    background: url("@/static/img/注意事项/流程1.png") no-repeat;
    background-size: 100% 100%;
  }
  .warning-info {
    margin-top: -10rpx;
    width: 100%;
    height: 500rpx;
    background: url("@/static/img/注意事项/底块.png") no-repeat;
    background-size: 100% 100%;
    padding: 20rpx;
  }
  .warning-info-title {
    // padding: 20rpx;
    font-size: 34rpx;
    margin-top: 20rpx;
  }
  .warning-info-content {
    font-size: 24rpx;
    color: #666666;
    letter-spacing: 1px;
    margin-top: 20rpx;
  }
  .process-info {
    font-size: 24rpx;
    color: #666666;
    line-height: 42rpx;
  }
  .prepare {
    font-size: 24rpx;
    margin: 30rpx 0;
    color: #000000;
  }
}
</style>
