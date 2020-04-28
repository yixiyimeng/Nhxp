<template>
	<mescroll-body ref="mescrollRef" @init="mescrollInit" @down="downCallback" @up="upCallback">
		<view v-for="(item,index) in dataSource" :key="index" class="account-item">
			<view class="flex justify-between">
				<div>平台消费</div>
				<view class="price">-128.00</view>
			</view>
			<view class="flex justify-between">
				<div>2020-04-21  12:12:56</div>
				<view>余额 <span class="margin-left-xs">1000.25</span></view>
			</view>
		</view>
		<view v-for="(item,index) in 2" :key="index" class="account-item">
			<view class="flex justify-between">
				<div>平台消费</div>
				<view class="price text-orange">+128.00</view>
			</view>
			<view class="flex justify-between">
				<div>2020-04-21  12:12:56</div>
				<view >余额 <span class="margin-left-xs">1000.25</span></view>
			</view>
		</view>
	</mescroll-body>
</template>

<script>
	import MescrollMixin from "@/components/mescroll-uni/mescroll-mixins.js";
	export default {
		mixins: [MescrollMixin], 
		data() {
			return {
				dataSource:10
			};
		},
		
	}
</script>

<style lang="scss">
.account-item{
	color: #a6a6a6;
	padding: 30upx 60upx;
	border-bottom: 1px solid #f0f0f0;
	font-size: 26upx;
	&>view:first-child{
		color: #000;
		font-size: 32upx;
		margin-bottom: 30upx;
		font-weight: blod;
	}
}
</style>
