<template>
	<view class="car_form">
		<u-form :model="userInfo" ref="uForm" labelPosition="left">
			<uni-card>
				<u-form-item
						v-for="(b,bi) in userInfo.base" :key="bi"
						class="u-form-item"
						:label="b.title"
						labelWidth="80" 
						:prop="b.name"
						borderBottom="true"
				>
					<u-input
						v-model="b.value"
						:placeholder="b.placeholder"
						:border="b.border"
						:type="b.type"
					></u-input>
				</u-form-item>
			</uni-card>
			<uni-card>
				<u-form-item class="u-form-item"  labelWidth="80" label="无车牌" prop="form.nonePlateNo">
					<u-switch class="nocard" slot="right" v-model="form.nonePlateNo" activeColor="#208eff" inactiveColor="rgb(230, 230, 230)" @change="cardchange"></u-switch>
				</u-form-item>
			</uni-card>
		<car-btn title="确定" style="margin-top: 0;" @click="submit"></car-btn> 
		</u-form>
	</view>
</template>
 
<script>
export default {
	data() {
		return {
			form: {
				username:''
			},
			userInfo:{
				base:[
					{
						title:'姓名',
						type:'text',
						name:'username',
						border:'none',
						value:'张三',
						placeholder:'请输入姓名',
						
					},
					{
						title:'手机',
						type:'number',
						name:'tel',
						border:'none',
						value:'18898875041',
						placeholder:'请输入姓名',
						
					}
				]
			}
		}
	},
	methods: {
		submit() {
			// if( this.form.username == false) return uni.$u.toast('请输入姓名');
			// if( !this.form.tel) return uni.$u.toast('请输入手机号码');
			// console.log(this.userInfo)
			var pages = getCurrentPages();
			var prevPage = pages[pages.length - 2]; //上一个页面
			console.log('6666666')
			console.log(prevPage)
			console.log('7777777')
			 //直接调用上一个页面的setData()方法，把数据存到上一个页面中去
			 // 上一个页面最后设置userdata
			 
			 prevPage.$vm.form = {name:'黎明'}
			  uni.navigateBack({//返回
					 delta: 1
			 })
		},

	}
};
</script> 

<style lang="scss" scoped>
.car_form{
	.u-form-item{
		margin: 10rpx auto;
		.u-radio-group{
			display: flex;
			flex-direction: row;
			flex-wrap: wrap;
		}
	}
}

</style>

