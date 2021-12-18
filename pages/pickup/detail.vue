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
		</view>
		<car-group title="当前工单" mode="card">
			<car-card class="uni-card" title="美容 $99" sub-title="2012-10-12 18:36:30"  :thumbnail="src" extra="待报价" :is-full="true">
				<view class="btn-container btn-order-container">
					<u-button
						class="action"
						text="支付"
						plain
						shape="circle"
						:customStyle="customStyles"
					></u-button>
					<u-button
						class="action"
						text="改价"
						plain
						shape="circle"
						:customStyle="customStyles"
					></u-button>
					<u-button
						class="action"
						text="打折"
						plain
						shape="circle"
						:customStyle="customStyles"
					></u-button>
					<u-button
						class="action"
						text="更多操作"
						plain
						shape="circle"
						:customStyle="customStyles"
					></u-button>
				</view>
			</car-card>
		</car-group>
		<car-group title="客户运营" mode="card">
			<customer-operations :list="cO_list"></customer-operations>
		</car-group>
		<car-group title="销售助手" mode="card">
		</car-group>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				src: 'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png',
				customStyles:{
					width:'auto',height:'auto',padding:'16rpx','font-size':'0.8em',color:'#3a3a3a'
				},
				cO_list: [
					{
						id:1,
						name:'保养到期',
						num:9,
						today:2
					},
					{
						id:2,
						name:'保险到期',
						num:2,
						today:0
					},
					{
						id:3,
						name:'回访',
						num:19,
						today:2
					},
					{
						id:4,
						name:'预约',
						num:19,
						today:2
					},
					{
						id:5,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:6,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:7,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:8,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:9,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:10,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:11,
						name:'流失预警',
						num:19,
						today:2
					}
				],
			}
		},
		onLoad() {
			
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
	.btn-order-container{
		width: 100%;
		.action{
			float: right;
			margin: 20rpx 0 30rpx 30rpx;
		}
	}
	
</style>
