<template>
	<view class="content head-bg" >
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<TabBar class="bom-tabbar" :pagePath="'/pages/Ashin/index'"></TabBar>
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
	  background-image: url('https://6d61-maydaysync-2gaijzhh7553fabf-1327815928.tcb.qcloud.la/maydayimgs/images/bg/ashin.jpg?sign=2928ff9272259a84b96506fe0716a394&t=1720705784');
	  background-size: 100% 100%;
	}
</style>
