<template>
  <div class="content">
    <img src="@/static/img/证件照/头图.png" class="upload-title-photo" alt="" />
    <div class="container">
      <div class="container-padding">
        <div class="login-info-title flex flexBetween">
          <div class="flex">
            <div class="title-info">1</div>
            <span class="title">基础信息</span>
          </div>
          <div class="flex login-info-next">
            <img src="@/static/img/身份证/下一项.png" alt="" />
            <span>下一项 身份证信息</span>
          </div>
        </div>
        <div class="check-container flex flexBetween">
          <div class="flex unit">
            部门：
            <picker @change="bindDateChange" :value="index" :range="array">
              <view class="uni-input">{{ array[index] }}</view>
            </picker>
          </div>
          <div class="flex unit">
            电话：
            <view class="uni-input">{{ phone }}</view>
          </div>
        </div>
        <div class="upload-photo flex flexBetween">
          <div>
            <div class="title">证件照</div>
            <div class="info">人脸正面半身照</div>
          </div>
          <div class="photo-bg" @click="handlerUpload">
            <img
              v-if="!fileUrl"
              class="photo-no-img"
              src="@/static/img/身份证/头像.png"
              alt=""
            />
            <img v-else class="photo-img" :src="fileUrl" alt="" />
          </div>
        </div>
        <div class="picture-title">拍摄标准</div>
        <div class="picture-list flex flexAround">
          <div class="picture-item">
            <img src="@/static/img/证件照/标准.png" alt="" />
            <div>标准拍摄</div>
          </div>
          <div class="picture-item">
            <img src="@/static/img/证件照/拍摄不全.png" alt="" />
            <div>拍摄不全</div>
          </div>
          <div class="picture-item">
            <img src="@/static/img/证件照/拍摄模糊.png" alt="" />
            <div>拍摄模糊</div>
          </div>
          <div class="picture-item">
            <img src="@/static/img/证件照/拍摄曝光.png" alt="" />
            <div>拍摄曝光</div>
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
      array: [
        "请选择",
        "机电队",
        "开拓四队",
        "开拓三队",
        "开拓一队",
        "运输队",
        "准备队"
      ],
      index: 0,
      phone: "18023568765",
      fileUrl: ""
    };
  },
  methods: {
    bindDateChange(e) {
      this.index = e.detail.value;
    },
    pageTo() {
      if (!this.fileUrl) {
        return uni.showToast({ title: "请上传证件照", icon: "none" });
      }
      uni.navigateTo({
        url: "/pages/register/identity"
      });
    },
    handlerUpload() {
      uni.chooseImage({
        count: 1, //默认9
        sizeType: ["original", "compressed"], //可以指定是原图还是压缩图，默认二者都有
        sourceType: ["album"], //从相册选择
        success: (res) => {
          // console.log(JSON.stringify(res.tempFilePaths));
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
  background: url("@/static/img/身份证/样式1.png") no-repeat;
}
</style>
