<template>
  <div class="wrap">
    <div class="header">视频</div>
    <div class="section">
      <div class="vido">
        <video
          vslide-gesture="true"
          show-fullscreen-btn="true"
          src="http://wxsnsdy.tc.qq.com/105/20210/snsdyvideodownload?filekey=30280201010421301f0201690402534804102ca905ce620b1241b726bc41dcff44e00204012882540400&bizid=1023&hy=SH&fileparam=302c020101042530230204136ffd93020457e3c4ff02024ef202031e8d7f02030f42400204045a320a0201000400"
        ></video>
      </div>
      <div class="client">
        <button @click="touch">获取更多视频</button>
        <div class="bodys" :style="{display:none}"></div>
        <div>非wifi状态下会消耗大量流量</div>
        <div class="shoop" @click="shop">
          <a :href='urls'>购买热门电影票</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      none: "none",
      urls:''
    };
  },
  methods: {
    touch: function() {
      if (this.none == "none") {
        this.none = "block";
      } else {
        this.none = "none";
      }
    },
    shop: function() {
      wx.request({
        url:
          "http://v.juhe.cn/wepiao/query?key=82403c8f0b5c8c5e567db4b78d6ec544",
        success: res => {
          this.urls = res.data.result.h5weixin;
        }
      });
    }
  }
};
</script>

<style>
.wrap {
  position: relative;
}
.section video {
  width: 100%;
}
.header {
  width: 100%;
  height: 40px;
  line-height: 40px;
  text-align: center;
  font-size: 18px;
  background: rgb(241, 241, 241);
}

.vido {
  height: 200px;
  background: red;
}
.section {
  flex: 1;
  display: flex;
  flex-direction: column;
}
.client {
  text-align: center;
}
.bodys {
  width: 100%;
  height: 270px;
  border: red;
  overflow-y: auto;
  border: 1px solid #cccc;
}
.shoop {
  font-size: 13px;
  border: 1px dashed black;
  width: 90px;
  position: absolute;
  bottom: 0;
  right: 0;
  z-index: 9999;
}
</style>
