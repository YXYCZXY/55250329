<template>
	<view class="uni-tabbar">
		<view class="uni-tabbar__item" v-for="(item,index) in tabbar" :key="index" @tap="changeTab(item)">
			<!-- 上面使用的是字体图标，解决切换页面的时候图标会闪的效果，毕竟每切换一个页面都会闪一下不太好看，可以切换使用下面的图片方式 -->
			<view v-if="true" class="uni-tabbar__bd">
				<view class="uni-tabbar__icon">
					<img v-if="item.pagePath == pagePath" class="uni-w-42 uni-h-42" :src="item.selectedIconPath" />
					<img v-else class="uni-w-42 uni-h-42" :src="item.iconPath" />
				</view>
			</view>
			<view class="uni-tabbar__label">
				{{item.text}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			pagePath: null
		},
		data() {
			return {
				page: 'contact',
				showPage: false,
				containerHeight: 400,
				tabbar: [{
						"pagePath": "/pages/Masa/index",
						"iconPath": "/static/bar-gs.png", //未选中tab图标路径
						"selectedIconPath": "/static/bar-gs.png", //选中tab图标路径
						"text": "",
					},
					{
						"pagePath": "/pages/Monster/index", //页面路径
						"text": "", //tab字体显示
						"iconPath": "/static/bar-ms.png", //未选中tab图标路径
						"selectedIconPath": "/static/bar-ms.png" //选中tab图标路径
					},
					{
						"pagePath": "/pages/Ashin/index", //页面路径
						"text": "", //tab字体显示
						"iconPath": "/static/bar-as.png", //未选中tab图标路径
						"selectedIconPath": "/static/bar-as.png" //选中tab图标路径
					},
					{
						"pagePath": "/pages/Stone/index", //页面路径
						"text": "", //tab字体显示
						"iconPath": "/static/bar-st.png", //未选中tab图标路径
						"selectedIconPath": "/static/bar-st.png" //选中tab图标路径
					},
					{
						"pagePath": "/pages/Ming/index", //页面路径
						"text": "", //tab字体显示
						"iconPath": "/static/bar-gy.png", //未选中tab图标路径
						"selectedIconPath": "/static/bar-gy.png" //选中tab图标路径
					}
				]
			};
		},
		onLoad() {
			console.log(this.pagePath)
		},
		methods: {
			changeTab(item) {
				let currentPage = item.pagePath;
				uni.showLoading({
					title: '正在加载...'
				})
				uni.redirectTo({
					url: currentPage,
					success: (e) => {
						uni.hideLoading();
					},
					fail: (e) => {
					}
				})
			},
		}
	}
</script>

<style lang="scss" scoped>
	.uni-tabbar {
		z-index: 999;
		width: 100%;
		height: 6%;
		display: flex;
		justify-content: space-around;
		
		padding: 7rpx 0;
		box-sizing: border-box;
		box-shadow: 0px 10px 20px 0px rgba(75, 51, 100, 0.05);
 
		.uni-tabbar__item {
			display: flex;
			flex-direction: column;
			.uni-tabbar__bd { // tabBar单项
				.uni-tabbar__icon { // tabBar图标
					width: 100rpx;
					height: 100rpx;
					img {
						width: 100%;
						height: 100%;
					}
				}
			}
 
			.uni-tabbar__label { // tabBar文字
				font-size: 22rpx;
				font-weight: 400;
				color: #D8DCE7;
				text-align: center;
				&.active {
					background-image: linear-gradient(to right top, #1CFDF1, #B330FF);
					font-size: 22rpx;
					-webkit-background-clip: text;
					-moz-background-clip: text;
					background-clip: text;
					box-decoration-break: clone;
					-webkit-box-decoration-break: clone;
					-moz-box-decoration-break: clone;
					color: transparent;
					position: relative;
				}
			}
		}
 
		// .uni-tabbar__icon {
		// 	height: 42upx;
		// 	line-height: 42upx;
		// 	text-align: center;
		// }
 
		.icon {
			display: inline-block;
		}
 
		// .uni-tabbar__label {
		// 	line-height: 24upx;
		// 	font-size: 24upx;
		// 	color: #999;
 
		// 	&.active {
		// 		color: #1ca6ec;
		// 	}
		// }
	}
</style>