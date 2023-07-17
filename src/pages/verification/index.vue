<template>
  <div class="content">
    <div class="container">
      <div class="verification-info flex">
        <img :src="imgUrl" alt="" />
        <div class="verification-info-container">
          <div class="verification-info-title flex">
            <div class="verification-name">{{ info.name }}</div>
            <div class="verification-sex">{{ info.sex }}</div>
          </div>
          <div>
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
      </div>
      <div class="tip">温馨提示：</div>
      <div class="tip-content">
        请核实个人信息，核实无误后，上传交管12123APP应用中>电子驾照>截图，点击“完成核验”按妞结束!
      </div>
      <div class="flex">
        <div class="verification-photo">
          <img
            @click="$refs.image.open()"
            src="@/static/img/heyan/zj.png"
            alt=""
          />
        </div>
        <div class="verification-photo" v-if="state == 'done'">
          <img src="@/static/img/heyan/hycg.png" alt="" />
        </div>
      </div>
      <div class="next-btn" @click="verify">
        {{ state == "done" ? "完成核验" : "核验" }}
      </div>
    </div>
    <uni-popup ref="image" type="center">
      <img
        @click="$refs.image.close()"
        style="width: 90%; margin-left: 5%"
        src="@/static/img/heyan/zj.png"
        alt=""
      />
    </uni-popup>
    <uni-popup ref="popup" type="center" @change="handlerChange">
      <div class="popup-container">
        <div class="label">核验通过</div>
      </div>
    </uni-popup>
  </div>
</template>
<script>
export default {
  data() {
    return {
      imgUrl: "https://img01.yzcdn.cn/vant/cat.jpeg",
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
}
.container {
  width: 96%;
  margin: 0 auto;
  padding-top: 20rpx;
}
.verification-info {
  height: 280rpx;
  background: url("@/static/img/heyan/bj.png") no-repeat;
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
    font-weight: 600;
  }
  .verification-info-container {
    align-items: flex-end;
    padding-left: 30rpx;
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
  background: url("@/static/img/heyan/yj.png") no-repeat;
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
  background: url("@/static/img/heyan/tg.png") no-repeat;
  background-size: 100% 100%;
  .label {
    color: #24c065;
    text-align: center;
    padding-top: 210rpx;
    font-family: en;
    font-size: 40rpx;
  }
}
</style>
