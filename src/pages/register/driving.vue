<template>
  <div class="content">
    <img src="@/static/img/jiashizheng/背景.png" class="upload-title-photo" alt="" />
    <div class="container">
      <div class="container-padding">
        <div class="login-info-title flex flexBetween">
          <div class="flex">
            <div class="title-info">3</div>
            <span class="title">驾驶证信息</span>
          </div>
          <div class="flex login-info-next">
            <img src="@/static/img/shenfenzheng/下一项.png" alt="" />
            <span>下一项 驾驶证信息</span>
          </div>
        </div>
        <div class="upload-photo flex flexBetween">
          <div>
            <div class="title">驾驶证</div>
            <div class="info">上传你的驾驶证照片</div>
          </div>
          <div class="photo-bg" @click="handlerUpload">
            <img
              v-if="!fileUrl"
              class="photo-no-img"
              src="@/static/img/jiashizheng/用户.png"
              style="width: 250rpx; height: 150rpx"
              alt=""
            />
            <img v-else class="photo-img" :src="fileUrl" alt="" />
          </div>
        </div>
        <div class="picture-title">拍摄标准</div>
        <div class="picture-list flex flexAround">
          <div class="picture-item">
            <img src="@/static/img/shenfenzheng/拍摄标准.png" alt="" />
            <div>标准拍摄</div>
          </div>
          <div class="picture-item">
            <img src="@/static/img/shenfenzheng/拍摄不全.png" alt="" />
            <div>拍摄不全</div>
          </div>
          <div class="picture-item">
            <img src="@/static/img/shenfenzheng/拍摄模糊.png" alt="" />
            <div>拍摄模糊</div>
          </div>
          <div class="picture-item">
            <img src="@/static/img/shenfenzheng/拍摄曝光.png" alt="" />
            <div>拍摄曝光</div>
          </div>
        </div>
        <div class="confirm-info-title flex">
          <img src="@/static/img/shenfenzheng/样式.png" alt="" />
          <span>请确认身份信息</span>
        </div>
        <div class="info-container">
          <div
            class="info-item flex"
            v-for="item in dataList"
            :key="item.label"
          >
            <div class="info-name">{{ item.label }}</div>
            ：
            <div class="info-label">{{ item.value }}</div>
          </div>
        </div>
        <div class="next-btn" @click="pageTo">提交身份信息</div>
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
      fileUrl: "",
      dataList: [
        {
          label: "姓名",
          value: "王立军"
        },
        {
          label: "准驾车型",
          value: "C1"
        },
        {
          label: "累计积分",
          value: "0分"
        },
        {
          label: "初次领证",
          value: "2018-0520"
        },
        {
          label: "状态",
          value: "正常"
        },
        {
          label: "证号",
          value: "1239874983759843639"
        },
        {
          label: "档案编号",
          value: "198759875943"
        },
        {
          label: "有效期限",
          value: "2018-05-20 至 2028-05-20"
        }
      ]
    };
  },
  methods: {
    // bindDateChange(e) {
    //   this.index = e.detail.value;
    // },
    pageTo() {
      if (!this.fileUrl) {
        return uni.showToast({ title: "请上传驾驶证照片", icon: "none" });
      }
      uni.showToast({ title: "提交成功，跳转至校验页面", icon: "loading" });
      setTimeout(() => {
        uni.navigateTo({
          url: "/pages/verification/index"
        });
      }, 600);
      //   uni.navigateTo({
      //     url: "/pages/register/driving"
      //   });
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
  background: url("@/static/img/shenfenzheng/样式1.png") no-repeat;
}
.picture-item {
  img {
    width: 160rpx;
    height: 120rpx;
  }
}
.info-container {
  //   height: 240rpx;
  width: 100%;
  background: url("@/static/img/shenfenzheng/信息背景.png") no-repeat;
  background-size: 100% 100%;
  padding-bottom: 30rpx;
}
.next-btn {
  margin-top: 30rpx;
}
</style>
