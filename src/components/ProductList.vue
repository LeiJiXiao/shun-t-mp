<template>
  <div>
    <ul class="taskList">
      <!--产品列表-->
      <li class="clearfix list">
        <div class="fl productImg"><image src="../../static/images/list.jpg" class="slide-image"></image></div>
        <div class="fl rightBar">
          <p class="title">出租商务车，大巴车，中巴车，结婚车，豪华车，私家车</p>
          <p class="desc">武汉顺推网络科技有限公司</p>
          <p class="price">固定佣金：500元/单</p>
        </div>
      </li>
      <li class="clearfix list">
        <div class="fl productImg"><image src="../../static/images/list.jpg" class="slide-image"></image></div>
        <div class="fl rightBar">
          <p class="title">出租商务车，大巴车，中巴车，结婚车，豪华车，私家车</p>
          <p class="desc">武汉顺推网络科技有限公司</p>
          <p class="price">固定佣金：500元/单</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['listData']
}
</script>

<style lang="scss" scoped>
  @import '../../static/_variable.scss';

  .taskList{
    background: #fff;
  li{
    padding: 25rpx 30rpx;
    border-bottom: 1px solid #F3F3F3;
  }
  .productImg{
    width: 183rpx;
    height: 136rpx;
    margin-right: 15rpx;
  .slide-image{
    width: 100%;
    height: 100%;
  }
  }
  .rightBar{
    font-size: $fs-golab-s;
    width: 475rpx;
    color: rgba(101,101,101,1);
  .title{
    color: #333;
    font-weight: 600;
  }
  .price{
    color:  $color-primary;
  }
  .desc{
    color: $color-8;
  }
  }
  }
</style>
