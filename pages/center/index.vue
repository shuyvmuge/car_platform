<template>
  <view class="page">
    <view class="top">
      <view class="background"></view>
    </view>
	
    <view class="user-card">
      <view class="card">
        <view class="top">
          <!-- <view class="userImage">
            <open-data type="userAvatarUrl"></open-data>
          </view> -->
		  <image src="/static/imgs/avatar.jpg" mode="aspectFit"></image>
        </view>
        <view class="bottom">
          <view class="left">
            <view class="user-text">
              <!-- <open-data type="userNickName"></open-data> -->
			  <text>中恒集团</text>
            </view>
            <view class="user-phone"> 171****4133 </view>
          </view>
          <view class="right flex-center">
            <u-icon class="icon" name="arrow-right"></u-icon>
          </view>
        </view>
      </view>
    </view>
	
    <view class="list-card">
      <view class="card">
        <view class="item item-bottom-solid">
          <view class="left flex-center">
            <image src="/static/imgs/store.png" mode="aspectFit"></image>
          </view>
          <view class="center">
            <text>店铺设置</text>
          </view>
          <view class="right flex-center">
            <u-icon class="icon" name="arrow-right"></u-icon>
          </view>
        </view>
      </view>
      <view class="card">
        <view class="item item-bottom-solid">
          <view class="left flex-center">
            <image src="/static/imgs/contact.png" mode="aspectFit"></image>
          </view>
          <view class="center">
            <text>联系客服</text>
          </view>
          <view class="right flex-center">
            <u-icon class="icon" name="arrow-right"></u-icon>
          </view>
        </view>
      </view>
	  <view class="card">
	    <view class="item item-bottom-solid">
	      <view class="left flex-center">
	        <image src="/static/imgs/xufei.png" mode="aspectFit"></image>
	      </view>
	      <view class="center">
	        <text>服务续费</text>
	      </view>
	      <view class="right flex-center">
	        <u-icon class="icon" name="arrow-right"></u-icon>
	      </view>
	    </view>
	  </view>
    </view>
	<car-btn title="退出登录"></car-btn>
  </view>
</template>
 <style lang="scss" scoped>
.top {
  height: 200rpx;
  position: relative;
  .background {
    background-color: #208eff;
    border-bottom-left-radius: 22px;
    border-bottom-right-radius: 22px;
    position: absolute;
    height: 300rpx;
    width: 100%;
  }
}
.icon {
  color: #96a1ae;
  font-size: 40rpx;
}
.user-card {
  height: 170rpx;
  padding: 0 30rpx;
  .card {
    position: relative;
    bottom: 66rpx;
    height: 250rpx;
    background-color: white;
    border-radius: 5px;
    .top {
      height: 30%;
      position: relative;
      image {
        position: absolute;
		bottom:15%;
		left:10%;
        width: 150rpx;
        height: 150rpx;
        overflow: hidden;
        border-radius: 50%;
        border: 2px solid white;
      }
    }
    .bottom {
      display: flex;
      height: 70%;
      .left {
		width: 84%;
        height: 100%;
        position: relative;
        .user-text {
          width: 100%;
          font-size: 1.1em;
          padding-left: 80rpx;
          height: 40%;
        }
        .user-phone {
          color: #96a1ae;
          padding-left: 80rpx;
          height: 50%;
          width: 100%;
          font-size: 0.9em;
        }
      }
      .right {
		  width: 10%;
        height: 50%;
      }
    }
  }
}
.list-card {
  padding: 0 30rpx;
  .card {
    border-radius: 10rpx;
    position: relative;
    background-color: white;
    border-radius: 10rpx;
    padding: 10rpx 30rpx;
    .item {
      display: flex;
      padding: 20rpx;
      .left {
        width: 10%;
        image {
          width: 40rpx;
          height: 40rpx;
        }
      }
      .center {
        width: 80%;
        display: flex;
        justify-content: start;
        align-items: center;
        font-size: 14px;
      }
      .right {
        justify-content: flex-end;
      }
    }
  }
}
.item-bottom-solid {
  border-bottom: 1px solid #d4d6da;
}

</style>
 
<script>
//import {  } from "@/common/api/{$}.js";
export default {
  data() {
    return {};
  },
  //监听页面初始化，其参数同 onLoad 参数，为上个页面传递的数据，参数类型为 Object（用于页面传参），触发时机早于 onLoad
  onInit() {},
  //监听页面加载，其参数为上个页面传递的数据，参数类型为 Object（用于页面传参）
  onLoad() {},
  //监听页面初次渲染完成。注意如果渲染速度快，会在页面进入动画完成前触发
  onReady() {},
  //监听页面显示。页面每次出现在屏幕上都触发，包括从下级页面点返回露出当前页面
  beforeDestroy() {},
  //页面滚动到底部的事件（不是scroll-view滚到底），常用于下拉下一页数据。
  onReachBottom() {},
  onShareAppMessage(res) {},
  created() {},
  methods: {},
};
</script>
