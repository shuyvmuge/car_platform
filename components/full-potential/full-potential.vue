<template>
	<view>
		<block v-for="(items,indexs) in list"  :key="indexs">
		<car-group :title="items.title" mode="card">
			<u-grid
					:border="false"
					:col="items.colNumber"
			>
				<u-grid-item
						v-for="(item,index) in items.iconsList"
						:key="index"
						 v-show="index > 6?kg:true"
				>
					<u-icon size="40" labelSize="14"
					:customStyle="{paddingTop:20+'rpx'}"
							:name="item.uIcon"
					></u-icon>
					<text class="grid-text">{{item.name}}</text>
				</u-grid-item>
				
				<u-grid-item  @click="kg = !kg" v-show="items.iconsList.length > 6">
					<u-icon  v-if="kg == false" label="展开" labelPos="bottom" size="28" labelSize="14" name="/static/imgs/zk.png"></u-icon>
					<u-icon  v-else label="收起" labelPos="bottom" size="28" labelSize="14" name="/static/imgs/sq.png"></u-icon>
				</u-grid-item>
			</u-grid>
		</car-group>
		</block>
	</view>
</template>
<script>
	/**
	 * 宫格的展示
	 * @description  依据ColorUI的宫格样式。只要以数组形式传入宫格
	 * @tutorial https://ext.dcloud.net.cn/plugin?id=5746
	 * @property {Array}  list 列表，用于传递数据（传递每一行宫格对象）
	 * @event {Function()} gridExc 若对象没有Url属性，点击宫格时传出该宫格的值
	 */
	export default {
		name: 'full-potential',
		props:{
			list: {
				type : Array,
				default: new Array
			}
		},
		data(){
			return{
				kg:false,
				tabber_list : this.list,		// 列表 , 由于参数不可改变值
			}
		},
		created:function(){
			
		},
		methods:{
			/** 连接到页或执行方法
			 * @param {Object} e
			 */
			navigateTo(e) {
				var url = e.currentTarget.dataset.url; // 连接的页面
				if (url != undefined) {
					// 跳转到页面
					uni.navigateTo({
						url: url
					});
				} else {
					var exec = e.currentTarget.dataset.exec;
					this.$emit("gridExc" ,e);			// 点击某一宫格时执行方法
				}
			},
			/** 展开或折叠当前宫格
			 * @param {Object} e
			 */
			showAllGrid(e) {
				var cur_grid = e.currentTarget.dataset.cur;
				// 获取当前列
				var tabber = this.tabber_list.find(function(item) {
					return item.cur == cur_grid;
				})
				if (tabber != undefined) {
					tabber.showAll = !tabber.showAll;
				}
			},
		}
	}
</script>
<style>
	
</style>
