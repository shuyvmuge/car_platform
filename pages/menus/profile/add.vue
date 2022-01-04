<template>
	<view class="car_form">
		<u-form :model="form" ref="uForm" labelPosition="left">
				<uni-card>
				<u-form-item class="u-form-item"  labelWidth="80" label="无车牌" prop="form.nonePlateNo">
					<u-switch class="nocard" slot="right" v-model="form.nonePlateNo" activeColor="#208eff" inactiveColor="rgb(230, 230, 230)" @change="cardchange"></u-switch>
				</u-form-item>
				<u-form-item
						v-show="form.nonePlateNo"
						class="u-form-item"
						label="备注:"
						labelWidth="80"
						prop="form.remarks"
						borderBottom="true"
				>
					<u-input
						v-model="form.remarks"
						disabledColor="#ffffff"
						placeholder="请备注说明"
						border="none"
					></u-input>
				</u-form-item>
				<u-form-item
						v-show="!form.nonePlateNo"
						class="u-form-item"
						label="车牌"
						labelWidth="80"
						prop="form.plateNo"
						borderBottom="true"
				>
					<view @click="plateShow = true">
						<u-input
							v-model="form.plateNo"
							disabled
							disabledColor="#ffffff"
							placeholder="请输入"
							border="none"
						></u-input>
					</view>
					<uni-plate-input v-if="plateShow" :plate="form.plateNo" @export="setPlate" @close="closeB"></uni-plate-input>
					<u-icon
						slot="right"
						name="scan"
						size="28"
					></u-icon>
				</u-form-item>
				<u-form-item
						class="u-form-item"
						label="品牌"
						labelWidth="80"
						prop="form.brand"
						borderBottom="true"
						@click="selectBrand"
				>
					<u-input
						v-model="form.brand"
						disabled
						disabledColor="#ffffff"
						placeholder="请输入品牌"
						border="none"
					></u-input>
				</u-form-item>
				<u-form-item
						class="u-form-item"
						label="车型"
						labelWidth="80"
						prop="form.cmodel"
						borderBottom="true"
				>
					<u-input
						v-model="form.cmodel"
						disabledColor="#ffffff"
						placeholder="请输入车型"
						border="none"
					></u-input>
				</u-form-item>
				</uni-card>
				<uni-card>
				<u-form-item
						class="u-form-item"
						label="姓名"
						labelWidth="80"
						prop="form.username"
						borderBottom="true"
				>
					<u-input
						v-model="form.username"
						disabledColor="#ffffff"
						placeholder="请输入车主姓名"
						border="none"
					></u-input>
				</u-form-item>
				<u-form-item
						class="u-form-item"
						label="手机"
						labelWidth="80" 
						prop="form.tel"
						borderBottom="true"
				>
					<u-input
						v-model="form.tel"
						disabledColor="#ffffff"
						placeholder="请输入客户手机"
						border="none"
						type="number"
					></u-input>
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
			plateNo: '',
			plateShow: false,
			remarks:'',
			form: {
				nonePlateNo:false,
				plateNo: this.plateNo,
				brand:'',
				cmodel:'',
				username:'',
				tel:''
			},
			orderTypes:[{
					typeId:1,
					name:'保养'
				},{
					typeId:2,
					name:'洗车'
				},{
					typeId:3,
					name:'施工单'
				},{
					typeId:4,
					name:'报价单'
				},{
					typeId:5,
					name:'定金单'
				},{
					typeId:6,
					name:'检车单'
				},{
					typeId:7,
					name:'保险单'
			}]
		}
	},
	onShow(){
		var that = this;
		var pages = getCurrentPages();

		console.log('33333333')
		console.log(pages[pages.length - 1].$vm.form.brand)//为传过来的值vm.form
		console.log('444444444')
	},
	methods: {
		submit() {
			if( this.form.nonePlateNo == false && !this.form.plateNo) return uni.$u.toast('请输入正确的车牌号');
			if( !this.form.orderType) return uni.$u.toast('请选择开单类型');
			uni.navigateTo({
				url:'/pages/pickup/firstsee'
			})
			console.log(this.form)
		},
		cardchange(){
			console.log('noplateNo')
		},
		selectBrand(){
			uni.navigateTo({
				url:'/pages/pickup/brand'
			})
		},
		setPlate(plate) {
			if (plate.length >= 7) this.form.plateNo = plate;
			this.plateShow = false;
		},
		closeB(){
			this.plateShow = false;
		}
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
