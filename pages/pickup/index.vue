<template>
	<view class="car_form">
		<u-form :model="form" ref="uForm" labelPosition="left">
				<uni-card>
				<u-form-item class="u-form-item"  labelWidth="80" label="无车牌" prop="form.nonumber">
					<u-switch class="nocard" slot="right" v-model="form.nonumber" activeColor="#208eff" inactiveColor="rgb(230, 230, 230)" @change="cardchange"></u-switch>
				</u-form-item>
				<u-form-item
						class="u-form-item"
						label="车牌"
						labelWidth="80"
						prop="form.number"
						borderBottom="true"
				>
					<view @click="plateShow = true">
						<u--input
							v-model="plateNo"
							disabled
							disabledColor="#ffffff"
							placeholder="请输入"
							border="none"
						></u--input>
					</view>
					<uni-plate-input v-if="plateShow" :plate="plateNo" @export="setPlate" @close="closeB"></uni-plate-input>
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
				>
					<u--input
						v-model="form.brand"
						disabledColor="#ffffff"
						placeholder="请输入品牌"
						border="none"
					></u--input>
				</u-form-item>
				<u-form-item
						class="u-form-item"
						label="车型"
						labelWidth="80"
						prop="form.cmodel"
						borderBottom="true"
				>
					<u--input
						v-model="form.cmodel"
						disabledColor="#ffffff"
						placeholder="请输入车型"
						border="none"
					></u--input>
				</u-form-item>
				<u-form-item
						class="u-form-item"
						label="公里数"
						labelWidth="80"
						prop="form.kl"
						borderBottom="true"
				>
					<u--input
						v-model="form.kl"
						disabledColor="#ffffff"
						placeholder="请输入公里数"
						border="none"
					></u--input>
				</u-form-item>
				</uni-card>
				<uni-card>
				<u-form-item
						class="u-form-item"
						label="姓名"
						labelWidth="80"
						prop="form.name"
						borderBottom="true"
				>
					<u--input
						v-model="form.name"
						disabledColor="#ffffff"
						placeholder="请输入车主姓名"
						border="none"
					></u--input>
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
					></u-input>
				</u-form-item>
				</uni-card>
				
				<uni-card >
				<u-form-item
						class="u-form-item"
						prop="form.standtype"
				>
				<u-radio-group
					class="u-radio-group"
				    v-model="form.standtype"
				    placement="row"
					shape="square"
				  >
				    <u-radio
				      :customStyle="{margin: 'auto 60rpx 60rpx 0'}"
				      v-for="(item, index) in radiolist1"
				      :key="index"
				      :label="item.name"
				      :name="item.name"
				    >
				    </u-radio>
				  </u-radio-group>
				</u-form-item> 
				</uni-card>
		<car-btn title="确定" style="margin-top: 0"></car-btn> 
		</u-form>
	</view>
</template>
 
<script>
export default {
	data() {
		return {
			plateNo: '',
			plateShow: false,
			form: {
				nonumber:0,
				number: '',
				brand:'',
				cmodel:'',
				kl:'',
				name:'',
				tel:'',
				standtype:'',
				fasttype:''
			},
			radiolist1:[{
					name:'保养'
				},{
					name:'洗车'
				},{
					name:'施工单'
				},{
					name:'报价单'
				},{
					name:'定金单'
				},{
					name:'检车单'
				},{
					name:'保险单'
			}],
			rules: {
				name: [
					{
						required: true,
						message: '请输入姓名',
						trigger: ['blur', 'change']
					}
				]
			}
		};
	},
	methods: {
		submit() {
			this.$refs.uForm.validate().then(res => {
				uni.$u.toast('校验通过')
			}).catch(errors => {
				uni.$u.toast('校验失败')
			})
		},
		setPlate(plate) {
			if (plate.length >= 7) this.plateNo = plate;
			this.plateShow = false;
		},
		closeB(){
			this.plateShow = false;
		}
	},
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
