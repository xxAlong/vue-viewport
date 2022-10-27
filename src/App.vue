<template>
  <div id="app">
    <div class="top">
      <div class="logo-wrap">
        <img src="./assets/tb.png" alt="">
      </div>
      <div class="logo-text">聊天APP</div>
    </div>
    <div class="mid">
      <div class="icon-wrap">
        <img src="./assets/ic.png" alt="">
      </div>
      <div class="download" @click="download">立即下载</div>
    </div>
    <div class="bot">
      <img src="./assets/sj.png" alt="">
    </div>
  </div>
</template>

<script>
import { iphoneAddress, androidAddress } from './config';
export default {
  name: 'App',
  data () {
    return {

    };
  },

  methods: {
    judeBrand () {
      var userAgent = navigator.userAgent.toLowerCase();
      console.log(navigator);
      var isIphone = userAgent.match(/(iphone|ipad|ipod)/i);
      var isHuawei = userAgent.match(/huawei/i);
      var isHonor = userAgent.match(/honor/i);
      var isOppo = userAgent.match(/oppo/i);
      var isOppoR15 = userAgent.match(/pacm00/i);
      var isVivo = userAgent.match(/vivo/i);
      var isXiaomi = userAgent.match(/mi\s/i);
      var isXIAOMI = userAgent.match(/xiaomi/i);
      var isXiaomi2s = userAgent.match(/mix\s/i);
      var isRedmi = userAgent.match(/redmi/i);

      if (isIphone) {
        return 'iphone';
      } else if (isHuawei || isHonor) {
        return 'huawei';
      } else if (isOppo || isOppoR15) {
        return 'oppo';
      } else if (isVivo) {
        return 'vivo';
      } else if (isXiaomi || isRedmi || isXiaomi2s || isXIAOMI) {
        return 'xiaomi';
      } else {
        return 'other';
      }
    },
    //添加跳转
    downLoadUrl (url) {
      // var a = document.createElement("a");
      // a.setAttribute("href", url);
      // a.click();
      window.location.href = url;
    },
    //具体跳转
    goDownload () {
      var iosLinkUrl = iphoneAddress;
      var androidLinkurl = androidAddress;
      var huaweiUrl = 'appmarket://details?id=com.xx.xxx';
      var oppoUrl = "oppomarket://details?packagename=com.xx.xxx";
      var vivoUrl = "vivomarket://details?id=com.xx.xxx";
      var xiaomiUrl = 'mimarket://details?id=com.xx.xxx';
      switch (this.judeBrand()) {
        case 'iphone':
          this.downLoadUrl(iosLinkUrl);
          break;
        case 'xiaomi':
          this.downLoadUrl(xiaomiUrl);
          break;
        case 'huawei':
          this.downLoadUrl(huaweiUrl);
          break;
        case 'vivo':
          this.downLoadUrl(vivoUrl);
          break;
        case 'oppo':
          this.downLoadUrl(oppoUrl);
          break;
        default:
          this.downLoadUrl(androidLinkurl);
          break;
      }
    },
    download () {
      this.goDownload();
    }
  }
};
</script>

<style lang="scss" >
img {
  display: block;
  width: 100%;
  height: 100%;
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: url('./assets/bg.png') no-repeat 0 0 transparent;
  background-size: 100% 100%;

  .top {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 131px;

    .logo-wrap {
      width: 120px;
      height: 120px;
    }

    .logo-text {
      font-size: 24px;
      font-weight: 700;
      height: 35px;
      line-height: 35px;
      margin-top: 9px;
    }
  }

  .mid {
    width: 190px;
    height: 44px;
    opacity: 1;
    border-radius: 23px;
    background: linear-gradient(180deg, rgba(133, 248, 164, 1) 0%, rgba(20, 205, 246, 1) 100%);
    border: 1px solid rgba(0, 0, 0, 0.2);
    margin-top: 55px;
    display: flex;
    justify-content: center;
    align-items: center;

    .icon-wrap {
      width: 21px;
      height: 14.06px;
      margin-right: 12px;
    }

    .download {
      font-size: 18px;
      font-weight: 400;
    }
  }

  .bot {
    width: 316.84px;
    height: 316.78px;
    margin-top: 100px;
  }
}
</style>
