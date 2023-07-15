<script>
export default {
  onLaunch: function () {
    console.log("App Launch");
  },
  onShow: function () {
    console.log("App Show");
  },
  onHide: function () {
    console.log("App Hide");
  }
};
</script>

<style lang="less">
@font-face {
  font-family: "c1";
  src: url("./static/font/Driod.ttf");
}
@font-face {
  font-family: "c2";
  src: url("./static/font/FZHLJW.TTF");
}
@font-face {
  font-family: "en";
  src: url("./static/font/PangMen.ttf");
}
.c1 {
  font-family: c1;
}
.c2 {
  font-family: c2;
}
.en {
  font-family: en;
}
/*每个页面公共css */
uni-page-body {
  height: 100%;
  .content {
    height: 100%;
    text-align: center;
    width: 100%;
    font-family: c1;
  }
}
.flex {
  display: flex;
  align-items: center;
}
.flexBetween {
  justify-content: space-between;
}
.flexAround {
  justify-content: space-around;
}
.flexCenter {
  justify-content: center;
}
img {
  height: 100%;
  width: 100%;
}
.next-btn {
  width: 400rpx;
  height: 86rpx;
  background: #1d60e8;
  color: white;
  text-align: center;
  line-height: 86rpx;
  margin: 120rpx auto 0;
  border-radius: 40rpx;
}
</style>
