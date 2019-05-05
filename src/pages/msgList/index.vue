<template>
  <div class="main">
    <ul class="list">
      <li @click="toDetail">
        <p>2019-10-12 10:12</p>
        <div><span class="label">推客</span>李某某</div>
        <div><i></i>推客向你推荐了新客户</div>
      </li>
    </ul>
  </div>
</template>

<script>
import { formatTime } from '@/utils/index'

export default {
  components: {},
  data () {
    return {}
  },
  methods: {
      toDetail() {
        wx.navigateTo({
          url: '/pages/follow/detail/main'
        })
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
  @import '../../../static/_variable.scss';

  .main {
    .list{
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
          height: 100rpx;
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
          color: $color-8;
          font-size: $fs-golab-m;
          position: relative;
          padding-left: 80rpx;
          i{
            position: absolute;
            left: 35rpx;
            top: 40rpx;
            width: 15rpx;
            height: 15rpx;
            background-color: $color-primary;
          }
        }
      }
    }
  }
</style>
