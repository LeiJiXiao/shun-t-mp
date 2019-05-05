<template>
  <div class="main">
    <header>
      <div>武汉顺推科技网络有限公司</div>
      <div>笑死伊朗</div>
      <div><text>李先生</text><span>客户刚刚补了班哔哩哔哩</span></div>
    </header>
    <ul class="list">
      <li>
        <p>2019-10-12 10:12</p>
        <div><span class="label">推客</span>李某某</div>
        <div><i></i>推客向你推荐了新客户</div>
      </li>
      <li>
        <p>2019-10-12 10:23</p>
        <div><span class="label">我</span>添加图片备注</div>
        <div class="imgBox">
          <image src="../../../../static/images/list2.jpg" class="slide-image" />
          <image src="../../../../static/images/list2.jpg" class="slide-image" />
        </div>
      </li>
    </ul>
    <footer>
      <div @click="toggle(1)">
        添加备注
        <ul class="menu" v-show="active ===  1">
          <li><a href="/pages/follow/addText/main">文字备注</a></li>
          <li><a href="/pages/follow/addImg/main">图片备注</a></li>
        </ul>
      </div>
      <div @click="toggle(2)">
        分组到
        <ul class="menu" v-show="active ===  2">
          <li>成交</li>
          <li>放弃</li>
          <li>跟进中</li>
        </ul>
      </div>
      <div @click="toggle(3)">
        支付
        <ul class="menu" v-show="active ===  3">
          <li><a href="/pages/follow/pay/main">支付佣金</a></li>
        </ul>
      </div>
      <div @click="toggle(4)">
        有效性
        <ul class="menu" v-show="active ===  4">
          <li><a href="/pages/follow/label/main">无效标记</a></li>
        </ul>
      </div>
    </footer>
  </div>
</template>

<script>
  import { formatTime } from '@/utils/index'

  export default {
    components: {
    },
    data () {
      return {
        active: 0
      }
    },
    methods: {
      toggle(curr) {
          this.active = this.active === curr? 0 : curr;
      }
    },
    created () {
      let logs
      if (mpvuePlatform === 'my') {
        logs = mpvue.getStorageSync({key: 'logs'}).data || []
      } else {
        logs = mpvue.getStorageSync('logs') || []
      }
      this.logs = logs.map(log => formatTime(new Date(log)))
    }
  }
</script>

<style lang="scss" scoped>
  @import '../../../../static/_variable.scss';

  .main {

  header{
    padding: 40rpx 0;
    background: #FFFAF4 url(../../../../static/images/icon5.jpg) no-repeat center bottom;
    @include background-size(30rpx, 30rpx)
    div{
      padding-left: 90rpx;
      color: $color-8;
      font-size: $fs-golab-l;
    }
    div:nth-child(1){
      margin-bottom: 20rpx;
      background: url(../../../../static/images/icon2.jpg) no-repeat 30rpx center;
      @include background-size(40rpx, 40rpx)
    }
    div:nth-child(2){
      margin-bottom: 40rpx;
      background: url(../../../../static/images/icon3.jpg) no-repeat 30rpx center;
      @include background-size(50rpx, 44px)
    }
    div:nth-child(3){
      background: url(../../../../static/images/icon4.jpg) no-repeat 30rpx center;
      @include background-size(44rpx, 42rpx);

      text{
        margin-right: 10rpx;
        @include fontStrong;
      }
      span{
        font-size: $fs-golab-s;
      }
    }
  }

  .list{
  .slide-image{
    width: 160rpx;
    height: 120rpx;
    margin-right: 10rpx;
  }
  li{
    font-size: $fs-golab-l;
  p{
    height: 75rpx;
    line-height: 75rpx;
    text-align: center;
    color: $color-8;
    font-size: $fs-golab-m;
  }
  div{
    color: $color-8;
    line-height: 100rpx;
    padding-left: 30rpx;
    background-color: #fff;
    border-bottom:1px solid #F5F5F3;
  .label{
    line-height: 1;
    display: inline-block;
    padding: 10rpx;
    background-color: #D3F1F1;
    border-radius: 10rpx;
    color: #2424F8;
    font-size: $fs-golab-m;
    margin-right: 30rpx;
  }
  }
  div:last-child{
    color: $color-3;
    font-size: $fs-golab-m;
    position: relative;
  }
  .imgBox{
    line-height: 100%;
    padding: 15rpx 30rpx;
  }
  }
  }
  footer{
    width: 100%;
    display: flex;
    background: #fff;
    padding: 20rpx 0;
    position: fixed;
    bottom: 0;
    left: 0;
    div{
      flex: 1;
      text-align: center;
      position: relative;
      border-right: 1px solid $color-3;
      @include fontStrong;
    }
    div:last-child{
      border-right: 0;
    }
    .menu{
      width: 100%;
      background-color: #fff;
      position: absolute;
      bottom: 62rpx;
      left: 0;
      li{
        width: 100%;
        line-height: 90rpx;
        text-align: center;
      }
    }
  }
  }
</style>
