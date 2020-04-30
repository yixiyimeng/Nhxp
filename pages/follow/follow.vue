<template>
	<view class="flex flex-direction pageview">
		<view class="topnav bg-white flex align-center justify-center">
			<span class="topnav-item active">产品</span>
			<span class="topnav-item">店铺</span>
		</view>
		<view class="main flex-sub"></view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">
	page,
	.pageview {
		height: 100%;
		width: 100%;
		overflow: hidden;

		.tabbar {
			box-shadow: 0 -5upx 5upx rgba(0, 0, 0, .1);
		}
	}
</style>
