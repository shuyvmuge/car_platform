<template>
	<view>
		<car-menu :menus="menus"></car-menu>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				menus: [{
						title: '成员管理',
						cur: 'applications',
						bgColor: 'bg-blue light', // 背景颜色
						color: 'blue',
						title_show: false,
						showAll: false,
						colNumber: 4, // 显示的列数
						menuItems: [{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'blue',
								name: '团队管理',
								url: '/pages/menus/team/index'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'blue',
								name: '客户档案',
								url: '/pages/menus/profile/index'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'blue',
								name: '项目表',
								url: '/pages/menus/item/index'
							}
						]
					},
					{
						title: '基础数据',
						cur: 'basic',
						bgColor: '', // 背景颜色
						color: 'blue',
						title_show: true,
						showAll: false,
						colNumber: 4, // 显示的列数
						menuItems: [{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'yellow',
								name: '基本信息',
								url: '/pages/toUrl/toUrl'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'blue',
								name: '员工管理',
								url: '/pages/toUrl/toUrl'
							},
			
						]
					}, {
						title: '产品目录',
						cur: 'goods',
						bgColor: '', // 背景颜色
						color: 'blue',
						title_show: true,
						showAll: false,
						colNumber: 4, // 显示的列数
						menuItems: [{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'yellow',
								name: '分类',
								url: '/pages/toUrl/toUrl'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'blue',
								name: '型号',
								url: '/pages/toUrl/toUrl'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'olive',
								name: '设备',
								url: '/pages/toUrl/toUrl'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'yellow',
								name: '常见问题',
								url: '/pages/toUrl/toUrl'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'yellow',
								name: '常见问题',
								url: '/pages/toUrl/toUrl'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'yellow',
								name: '常见问题',
								url: '/pages/toUrl/toUrl'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'yellow',
								name: '常见问题',
								url: '/pages/toUrl/toUrl'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'yellow',
								name: '常见问题',
								url: '/pages/toUrl/toUrl'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'yellow',
								name: '常见问题',
								url: '/pages/toUrl/toUrl'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'yellow',
								name: '常见问题',
								url: '/pages/toUrl/toUrl'
							},
							{
								uIcon: 'https://www.uviewui.com/common/logo.png',
								color: 'yellow',
								name: '常见问题',
								url: '/pages/toUrl/toUrl'
							}
						]
					},
					{
						title: '权限管理',
						cur: 'goods',
						bgColor: '', // 背景颜色
						color: 'blue',
						title_show: true,
						showAll: false,
						colNumber: 4, // 显示的列数
						menuItems: [{
							uIcon: 'https://www.uviewui.com/common/logo.png',
							color: 'red',
							name: '权限设置',
							url: '/pages/toUrl/toUrl'
						}]
					}
				]
			}
		},
		onLoad() {
		}
	}
</script>

<style>
</style>
