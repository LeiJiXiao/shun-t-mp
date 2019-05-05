<template>
  <div class="main">
    <swiper
      :autoplay="true"
      :interval="3000"
      :duration="500">
      <swiper-item>
        <image :src="bannerUrl" class="slide-image" />
      </swiper-item>
    </swiper>
    <div class="newRec">
      <h2><a href="/pages/msgList/main">收到新客户推荐</a></h2>
      <span></span>
    </div>
    <div class="cateList">
      <ul>
        <li class="title">收到推荐</li>
        <li>跟进中</li>
        <li>成交</li>
        <li>放弃</li>
      </ul>
    </div>
    <div class="gutter"></div>
    <div class="taskArea">
      <ul class="tab">
        <li :class="{active: tab === 1}" @click="tab =1">销售任务</li>
        <li :class="{active: tab === 2}" @click="tab =2">附近的任务</li>
        <li :class="{active: tab === 3}" @click="tab =3">收藏</li>
      </ul>
      <div class="search">
        <div><a href="/pages/search/main"><span>搜索</span><icon type="search" size="16"/></a></div>
      </div>
      <ProductList></ProductList>
    </div>
  </div>
</template>

<script>
  import ProductList from '@/components/ProductList';

  export default {
    data () {
      return {
        bannerUrl: '../../static/images/banner.jpg',
        tab: 1
      }
    },
    components: {
      ProductList
    },
    methods: {
      bindViewTap () {
        const url = '../logs/main'
        if (mpvuePlatform === 'wx') {
          mpvue.switchTab({ url })
        } else {
          mpvue.navigateTo({ url })
        }
      },
      clickHandle (ev) {
        console.log('clickHandle:', ev)
        // throw {message: 'custom test'}
      }
    },

    created () {
      //let app = getApp()
      //console.log("app", app)
    }
  }
</script>

<style lang="scss" scoped>
  @import '../../../static/_variable.scss';

  .gutter{
    @include gutter(15rpx);
  }
  swiper{
    height: 390rpx;
    .slide-image{
      width: 100%;
      height: 390rpx;
    }
  }
  .newRec{
    box-sizing: border-box;
    height: 112rpx;
    background-color: #F5F5F3;
    padding-top: 18rpx;
    position: relative;
    h2{
      width: 90%;
      margin: 0 auto;
      height: 80rpx;
      line-height: 80rpx;
      border-radius: 50rpx;
      background-color: #fff;
      text-align: center;
      @include fontStrong;
    }
    span{
      position: absolute;
      width: 15rpx;
      height: 15rpx;
      background-color: $color-primary;
      border-radius: 50%;
      left: 32%;
      top: 45rpx;
    }
  }
  .cateList{
    background-color: #fff;
    ul{
      li{
        height: 100rpx;
        line-height: 100rpx;
        border-bottom:1px solid #F5F5F3;
        padding-left: 40rpx;
        color: #363636;
        font-size: $fs-golab-l;
      }
      .title{
        background: url(../../../static/images/icon.jpg) no-repeat 40rpx center;
        background-size: 45rpx 45rpx;
        padding-left: 95rpx;
        @include fontStrong;
      }
    }
  }
  .taskArea{
    background-color: #fff;
    .tab{
      padding-left: 40rpx;
      li{
        display: inline-block;
        margin-right: 40rpx;
        height: 100rpx;
        line-height: 100rpx;
        @include fontStrong;
      }
      .active{
        color: $color-primary;
      }
    }
    .search{
      padding-bottom: 30rpx;
      border-bottom: 1px solid #F3F3F3;
      div{
        width: 95%;
        margin: 0 auto;
        height: 60rpx;
        line-height: 60rpx;
        border: 1px solid #8F8F8F;
        border-radius: 5px;
        text-align: center;
        color: $color-8;
        font-size: 28rpx;
        span{
          margin-right: 10rpx;
        }
        icon{
          position: relative;
          top: 10rpx;
        }
      }
    }
  }
</style>
