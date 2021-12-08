<template>
	<view class="car_form">
		<u--form :model="form" ref="uForm" labelPosition="left">
			<uni-group title="车辆信息" mode="card">
				<u-form-item class="u-form-item"  labelWidth="80" label="无车牌" prop="form.nonumber">
					<u-switch class="nocard" slot="right" v-model="form.nonumber" activeColor="#208eff" inactiveColor="rgb(230, 230, 230)" @change="cardchange"></u-switch>
				</u-form-item>
				<u-form-item
						class="u-form-item"
						label="车牌"
						labelWidth="80"
						prop="form.number"
						borderBottom="true"
						@click="showNumber"
				>
					<u--input
						v-model="form.number"
						disabled
						disabledColor="#ffffff"
						placeholder="请输入"
						border="none"
					></u--input>
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
						v-model="form.brand"
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
						placeholder="请输入车型"
						border="none"
					></u--input>
				</u-form-item>
			</uni-group>
			
			<uni-group title="车主信息" mode="card">
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
					<u--input
						v-model="form.tel"
						disabledColor="#ffffff"
						placeholder="请输入客户手机"
						border="none"
					></u--input>
				</u-form-item>
			</uni-group>
			<uni-group title="开单类型" mode="card">
				<u-form-item
						class="u-form-item"
						label=""
						prop="form.standtype"
				>
				<!-- <view class="scroll">
					<view class="scroll_item">
						
					</view>
				</view> -->
				<u-radio-group
					class="u-radio-group"
				    v-model="form.standtype"
				    placement="row"
					shape="square"
				  >
				    <u-radio
				      :customStyle="{marginBottom: '8px'}"
				      v-for="(item, index) in radiolist1"
				      :key="index"
				      :label="item.name"
				      :name="item.name"
				    >
				    </u-radio>
				  </u-radio-group>
				</u-form-item> 
			</uni-group>
		</u--form>
		
		</u--form>
	</view>
</template>

<script>
export default {
	data() {
		return {
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
			radiolist1:[
				{
					name:'meinv'
				},{
					name:'meinv'
				},{
					name:'meinv'
				},{
					name:'meinv'
				},{
					name:'meinv'
				}
			],
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
		showNumber(){
			console.log(1)
		}
	},
};
</script> 

<style lang="scss" scoped>
.car_form{
	margin: 30rpx;
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
