<template>
	<view class="evaluate-item">
		<div class="title flex justify-between">
			<span>购买商：方德玫瑰</span>
			<tui-rate :current="index" @change="change" :size="14"></tui-rate>
		</div>
		<div class="info">玫瑰保护的很好，值得回购！送达时间快，接收
			不便时还可以送到指定地点，花也是新鲜的。
		</div>
		<div class="flex justify-between">
			<span>2020-03-01 11:00:50</span>
			<span>订单号：abc147258369</span>
		</div>
	</view>
</template>

<script>
	import tuiRate from "@/components/rate/rate"
	export default {
		data() {
			return {
				index: 4
			};
		},
		components: {
			tuiRate
		},
		methods: {
			change: function(e) {
				this.index = e.index;
			}
		}
	}
</script>

<style lang="scss">
	.evaluate-item {
		margin: 20upx 30upx 0;
		background: #fff;
		box-shadow: 0px 4upx 16upx 0px rgba(213, 213, 213, 1);
		border-radius: 8upx;
		padding: 34upx 24upx;
		color: #ABABAB;
		font-size: 24upx;

		.title {
			color: #1D1D1D;
			font-size: 30upx;
		}

		.info {
			color: #5F5F5F;
			font-size: 28upx;
			margin: 25upx 0;
			line-height: 40upx;
		}
	}
</style>
