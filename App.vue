<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	/* 注意要写在第一行，同时给style标签加入lang="scss"属性 */
	@import "@/uni_modules/uview-ui/index.scss";
	page {
			background-color: #FFFFFF;
			font-size: 28rpx;
			color: #272e2d;
			font-family: Helvetica Neue, Helvetica, sans-serif;
		}
		view,
		scroll-view,
		swiper,
		button,
		input,
		textarea,
		label,
		navigator,
		image {
			box-sizing: border-box;
		}
		.car-hover{
			:active{
				opacity: .5;
			}
		}
</style>