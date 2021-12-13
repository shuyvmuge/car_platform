<template>
	<view class="car_detail">
		<view class="car_header">
			<uni-card title="苏B99999" sub-title="18898875042" :thumbnail="src" :is-full="true">
				<view class="btn-container">
					<u-button
						text="消费记录"
						plain
						shape="circle"
						:customStyle="customStyles"
					></u-button>
					<u-button
						icon="plus-people-fill"
						plain
						shape="circle"
						:customStyle="customStyles"
					></u-button>
					<u-button
						icon="phone-fill"
						plain
						shape="circle"
						:customStyle="customStyles"
					></u-button>
					<u-button
						icon="edit-pen-fill"
						plain
						shape="circle"
						:customStyle="customStyles"
					></u-button>
				</view>
			</uni-card>
				
			<car-group title="当前工单" mode="card">
				<uni-card title="美容 $99" sub-title="2012-10-12 18:36:30"  :thumbnail="src" extra="待报价" :is-full="true">
					<view class="btn-container">
						<u-button
							text="更多操作"
							plain
							shape="circle"
							:customStyle="customStyles"
						></u-button>
						<u-button
							text="改价"
							plain
							shape="circle"
							:customStyle="customStyles"
						></u-button>
						<u-button
							text="打折"
							plain
							shape="circle"
							:customStyle="customStyles"
						></u-button>
						<u-button
							text="支付"
							plain
							shape="circle"
							:customStyle="customStyles"
						></u-button>
					</view>
				</uni-card>
			</car-group>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				src: 'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png',
				customStyles:{
					width:'auto',height:'auto',padding:'10rpx','font-size':'0.8em',
				}
			}
		}
	}
</script>

<style lang="scss">
	.car_header{
		.btn-container{
			width: 80%;
			display: flex;
			flex-direction: row;
			justify-content: flex-start;
			align-items: flex-start;
		}
	}
	
</style>
