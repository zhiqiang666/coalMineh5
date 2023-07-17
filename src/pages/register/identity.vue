<template>
  <div class="content">
    <img src="@/static/img/shenfenzheng/tt.png" class="upload-title-photo" alt="" />
    <div class="container">
      <div class="container-padding">
        <div class="login-info-title flex flexBetween">
          <div class="flex">
            <div class="title-info">2</div>
            <span class="title">身份证信息</span>
          </div>
          <div class="flex login-info-next">
            <img src="@/static/img/shenfenzheng/xyx.png" alt="" />
            <span>下一项 驾驶证信息</span>
          </div>
        </div>
        <div class="upload-photo flex flexBetween">
          <div>
            <div class="title">身份证</div>
            <div class="info">上传你身份证头像面</div>
          </div>
          <div class="photo-bg" @click="handlerUpload">
            <img
              v-if="!fileUrl"
              class="photo-no-img"
              src="@/static/img/shenfenzheng/yh.png"
              style="width: 250rpx; height: 150rpx"
              alt=""
            />
            <img v-else class="photo-img" :src="fileUrl" alt="" />
          </div>
        </div>
        <div class="picture-title">拍摄标准</div>
        <div class="picture-list flex flexAround">
          <div class="picture-item">
            <img src="@/static/img/shenfenzheng/psbz.png" alt="" />
            <div>标准拍摄</div>
          </div>
          <div class="picture-item">
            <img src="@/static/img/shenfenzheng/psbq.png" alt="" />
            <div>拍摄不全</div>
          </div>
          <div class="picture-item">
            <img src="@/static/img/shenfenzheng/psmh.png" alt="" />
            <div>拍摄模糊</div>
          </div>
          <div class="picture-item">
            <img src="@/static/img/shenfenzheng/psbg.png" alt="" />
            <div>拍摄曝光</div>
          </div>
        </div>
        <div class="confirm-info-title flex">
          <img src="@/static/img/shenfenzheng/ys.png" alt="" />
          <span>请确认身份信息</span>
        </div>
        <div class="info-container">
          <div class="info-item flex">
            <div class="info-name">姓名</div>
            ：
            <div class="info-label">{{ name }}</div>
          </div>
          <div class="info-item flex">
            <div class="info-name">身份证号</div>
            ：
            <div class="info-label">{{ idno }}</div>
          </div>
          <div class="info-item flex">
            <div class="info-name">有效期</div>
            ：
            <div class="info-label">{{ time[0] }} 至 {{ time[1] }}</div>
          </div>
        </div>
        <div class="next-btn" @click="pageTo">下一步</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: "王立军",
      idno: "12982367859463853469",
      time: ["2018-05-22", "2022-05-22"],
      fileUrl: ""
    };
  },
  methods: {
    // bindDateChange(e) {
    //   this.index = e.detail.value;
    // },
    pageTo() {
      if (!this.fileUrl) {
        return uni.showToast({ title: "请上传身份证照片", icon: "none" });
      }
      uni.navigateTo({
        url: "/pages/register/driving"
      });
    },
    handlerUpload() {
      uni.chooseImage({
        count: 1, //默认9
        sizeType: ["original", "compressed"], //可以指定是原图还是压缩图，默认二者都有
        sourceType: ["album"], //从相册选择
        success: (res) => {
          this.fileUrl = res.tempFilePaths[0];
        }
      });
    }
  }
};
</script>
<style scoped lang="less">
@import "@/static/style/loginCommon.less";
.title-info {
  background: url("@/static/img/shenfenzheng/ys1.png") no-repeat;
}
.picture-item {
  img {
    width: 160rpx;
    height: 120rpx;
  }
}
.info-container {
  height: 240rpx;
  width: 100%;
  background: url("@/static/img/shenfenzheng/xxbj.png") no-repeat;
}
</style>
