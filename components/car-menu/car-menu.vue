<template>
	<view>
		<block v-for="(items,i) in menus"  :key="i">
		<car-group :title="items.title" mode="card">
			<view class="menu-container">
				<u-grid
						:border="false"
						:col="items.colNumber"
				>
					<u-grid-item
							v-for="(item,j) in items.menuItems"
							:key="j"
							v-show="j > 6?kg:true"
					>
						<view class="auth-item" @click="jumpPage(item)">
							<u-icon size="50" labelSize="14"
							:customStyle="{padding:20+'rpx'}"
									:name="item.uIcon"
							></u-icon>
							<text class="grid-text">{{item.name}}</text>
						</view>
						
					</u-grid-item>
					
					<u-grid-item  @click="kg = !kg" v-show="items.menuItems.length > 6">
						<view class="auth-item">
							<u-icon  v-if="kg == false" label="展开" labelPos="bottom" size="28" labelSize="14" name="/static/imgs/zk.png"></u-icon>
							<u-icon  v-else label="收起" labelPos="bottom" size="28" labelSize="14" name="/static/imgs/sq.png"></u-icon>
						</view>
					</u-grid-item>
				</u-grid>
			</view>
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
		name: 'CarMenu',
		props:{
			menus: {
				type : Array,
				default: new Array
			}
		},
		data(){
			return{
				kg:false
			}
		},
		created:function(){
			
		},
		methods:{
			jumpPage(item) {
				console.log(item)
				var title = item.name?item.name:''
				var url = item.url+'?title='+title
				if (url != undefined) {
					// 跳转到页面
					uni.navigateTo({
						url: url
					});
				}
			},
	
		}
	}
</script>
<style scoped>
	.menu-container{
		margin-bottom: 30rpx;
	}
	.auth-item{
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin: 10rpx;
	}
</style>
