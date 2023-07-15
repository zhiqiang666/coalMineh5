<template>
  <div class="content">
    <div class="result-container flex flexBetween">
      <div>审核结果:</div>
      <div :class="['result-state', 'state-' + resultState]">
        <span v-if="resultState == 'success'">审核通过</span>
        <span v-if="resultState == 'error'">审核失败</span>
        <span v-if="resultState == 'normal'">未审核</span>
      </div>
    </div>
    <div class="container">
      <div class="verification-info flex">
        <div>
          <img :src="imgUrl" alt="" />
          <div class="verification-name">{{ info.name }}</div>
        </div>
        <div class="verification-info-container">
          <!-- <div class="verification-info-title flex">
            <div class="verification-name">{{ info.name }}</div>
          </div> -->
          <div class="verification-item flex">
            <div class="verification-item-name">登记时间</div>
            <div class="verification-item-value">{{ info.time }}</div>
          </div>
          <div class="verification-item flex">
            <div class="verification-item-name">手机号码</div>
            <div class="verification-item-value">{{ info.phone }}</div>
          </div>
          <div class="verification-item flex">
            <div class="verification-item-name">所属部门</div>
            <div class="verification-item-value">{{ info.unit }}</div>
          </div>
          <div class="verification-item flex">
            <div class="verification-item-name">证件号码</div>
            <div class="verification-item-value">{{ info.no }}</div>
          </div>
        </div>
      </div>
      <div class="card-container">
        <div
          :class="['card-list card-photo', photoMap.userError && 'card-error']"
          style="margin-top: 12rpx"
        >
          <img :src="photoMap.userPhoto" alt="" />
          <div class="tip">证件照</div>
        </div>
        <div :class="['card-list card-id', photoMap.idError && 'card-error']">
          <img :src="photoMap.idPhoto" alt="" />
          <div class="tip">身份证</div>
        </div>
        <div
          :class="[
            'card-list card-driver',
            photoMap.driverError && 'card-error'
          ]"
        >
          <img :src="photoMap.driverPhoto" alt="" />
          <div class="tip">驾驶证</div>
        </div>
      </div>
      <div class="footer-tip">
        温馨提示：标红区域信息错误，可进行修改重新上传
      </div>
    </div>
    <div class="next-btn" @click="handlerPageTo" v-if="resultState == 'normal'">
      重新提交
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      resultState: "normal", //success 是通过 error是失败 normal未审核
      imgUrl: "https://img01.yzcdn.cn/vant/cat.jpeg",
      photoMap: {
        userPhoto: "/static/img/审核结果/证件照.png",
        idPhoto: "/static/img/审核结果/身份证.png",
        driverPhoto: "/static/img/审核结果/驾驶证.png",
        userError: true,
        idError: false,
        driverError: true
      },
      state: "",
      info: {
        name: "王罗浩",
        sex: "男",
        time: "2018-0620",
        phone: "18329878777",
        unit: "机电部",
        no: "192873926965726943"
      }
    };
  },
  methods: {
    handlerPageTo() {
      uni.navigateTo({
        url: "/pages/register/index"
      });
    },
    verify() {
      if (this.state === "done") {
        uni.showToast({
          title: "核检已完成,即将跳转至首页",
          icon: "loading"
        });
        setTimeout(() => {
          uni.navigateTo({
            url: "/pages/index/index"
          });
        }, 1200);
      } else {
        this.$refs.popup.open();
        setTimeout(() => {
          this.$refs.popup.close();
        }, 2000);
      }
    },
    handlerChange(e) {
      if (!e.show) {
        this.state = "done";
      }
    }
  }
};
</script>

<style scoped lang="less">
.content {
  background: #f1f1f1;
  text-align: left;
  height: auto;
  overflow: hidden;
}
.container {
  width: 96%;
  margin: 0 auto;
  padding-top: 20rpx;
}
.verification-info {
  height: 316rpx;
  background: url("@/static/img/审核结果/卡片背景.png") no-repeat;
  background-size: 100% 100%;
  font-size: 24rpx;
  img {
    width: 170rpx;
    height: 210rpx;
    margin-left: 40rpx;
    border-radius: 10rpx;
  }
  .verification-name {
    font-size: 34rpx;
    text-align: center;
    margin-left: 24rpx;
  }
  .verification-info-container {
    align-items: flex-end;
    padding-left: 30rpx;
    margin-top: -40rpx;
  }
  .verification-item-name {
    width: 118rpx;
    text-align: left;
  }
}
.verification-info-title {
  align-items: flex-end;
  padding-bottom: 12rpx;
  .verification-sex {
    padding-left: 30rpx;
  }
}
.tip {
  font-size: 28rpx;
  margin-top: 20rpx;
  margin-bottom: 12rpx;
  padding: 0 40rpx;
}
.tip-content {
  font-size: 24rpx;
  color: #666;
  letter-spacing: 1px;
  padding: 0 40rpx;
}
.verification-photo {
  width: 280rpx;
  height: 524rpx;
  margin: 50rpx auto 0;
  background: url("@/static/img/核验/圆角.png") no-repeat;
  background-size: 100% 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  img {
    width: 90%;
    height: 90%;
  }
}
.popup-container {
  width: 400rpx;
  height: 310rpx;
  background: url("@/static/img/核验/通过.png") no-repeat;
  background-size: 100% 100%;
  .label {
    color: #24c065;
    text-align: center;
    padding-top: 210rpx;
    font-family: en;
    font-size: 40rpx;
  }
}
.verification-item {
  line-height: 50rpx;
}
.card-container {
  padding: 0 12rpx;
}
.card-list {
  height: 390rpx;
  width: 100%;
  background: white;
  border-radius: 16rpx;
  margin-top: 24rpx;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  img {
    width: 590rpx;
    height: 280rpx;
  }
  .tip {
    position: absolute;
    width: 100%;
    text-align: center;
    bottom: 20rpx;
  }
}
.result-container {
  height: 100rpx;
  background: white;
  padding: 0 36rpx;
  font-size: 28rpx;
}
.result-state {
  font-family: en;
  font-size: 34rpx;
  border: 1px solid red;
  border-radius: 10rpx;
  padding: 6rpx 10rpx;
}
.state-success {
  color: #03ae5f;
  border-color: #03ae5f;
}
.state-error {
  color: #ae0303;
  border-color: #ae0303;
}
.state-normal {
  color: #666666;
  border-color: #666666;
}
.next-btn {
  margin-top: 30rpx;
  width: 500rpx;
}
.footer-tip {
  color: #ae0303;
  font-size: 24rpx;
  padding: 20rpx 20rpx 0;
}
.card-error {
  border: 1px solid #ae0303;
}
</style>
