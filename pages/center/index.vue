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
		  <image :src="store.logo" mode="aspectFit"></image>
        </view>
        <view class="bottom">
          <view class="left car-hover">
            <view class="user-text">
			  <text>{{store.name}}</text>
            </view>
            <view class="user-phone"> {{store.phone}} </view>
          </view>
          <view class="right flex-center">
            <u-icon class="icon" name="arrow-right"></u-icon>
          </view>
        </view>
      </view>
    </view>
	
    <view class="list-card">
      <view 
		class="card car-hover" 
		v-for="(item,index) in menus" 
		:key="index"
	>
        <view class="item item-bottom-solid" @click="menuAction(item)">
          <view class="left flex-center">
            <image :src="item.icon" mode="aspectFit"></image>
          </view>
          <view class="center">
            <text>{{item.name}}</text>
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
  // border-bottom: 1px solid #d4d6da;
}

</style>
 
<script>
//import {  } from "@/common/api/{$}.js";
export default {
  data() {
    return {
		store:{
			name:'华兰生物',
			logo:'/static/imgs/avatar.jpg',
			phone:'1238644335'
		},
		menus:[
			{	id:1,
				name:'店铺设置',
				icon:'/static/imgs/store.png',
				url:''
			},
			{	id:1,
				name:'联系客服',
				icon:'/static/imgs/contact.png',
				url:''
			},
			{	id:1,
				name:'服务续费',
				icon:'/static/imgs/xufei.png',
				url:''
			}
		]
	};
  },
  methods: {
	  menuAction(menu){
		  console.log(menu)
	  }
  },
};
</script>
