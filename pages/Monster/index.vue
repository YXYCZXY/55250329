<template>
	<view class="content head-bg" >
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<TabBar class="bom-tabbar" :pagePath="'/pages/show/index'"></TabBar>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	.head-bg{
	  height: 100vh;
	  background-image: url('https://6d61-maydaysync-2gaijzhh7553fabf-1327815928.tcb.qcloud.la/maydayimgs/images/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20240709214825.jpg?sign=941e47e17ceed873f78658de77fb51bf&t=1720532934');
	  background-size: 100% 100%;
	}
</style>
