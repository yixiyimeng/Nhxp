<template>
	<view>
		<view class="toptitle flex align-center">
			<image src="/static/shop/prompt@2x.png" mode="widthFix"></image>
			<view class="flex-sub">
				该统计表统计数据实时更新，方便供货商
				备货，最终供货总数以交易结束为准。
			</view>
			<view class="btn flex align-center">
				<image src="/static/shop/refresh@2x.png" mode="widthFix"></image>
				<text>刷新</text>
			</view>
		</view>
		<view class="tablebox">
			<view class="table">
				<view class="table-hd flex">
					<span>品种</span>
					<span class="flex-sub">属性</span>
					<span>数量</span>
					<span>单价</span>
					<span>单价</span>
				</view>
				<view class="table-bd">
					<view class="table-td flex">
						<span>红玫瑰</span>
						<span class="flex-sub">A级；20支/扎；中熟</span>
						<span>5</span>
						<span>5</span>
						<span>25</span>
					</view>
					<view class="table-td flex">
						<span>红玫瑰</span>
						<span class="flex-sub">A级；20支/扎；中熟</span>
						<span>5</span>
						<span>5</span>
						<span>25</span>
					</view>
					<view class="table-td flex">
						<span>红玫瑰</span>
						<span class="flex-sub">A级；20支/扎；中熟</span>
						<span>5</span>
						<span>5</span>
						<span>25</span>
					</view>
				</view>
				<view class="table-ft flex">
					<span class="flex-sub text-right">合计:</span>
					<span>15</span>
					<span>14</span>
					<span>15</span>
				</view>
			</view>
		</view>
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
	.toptitle {
		padding: 24upx 30upx;
		color: #545454;
		font-size: 26upx;
		background: #F7F7F7;
		line-height: 36upx;

		image {
			width: 48upx;
		}

		&>text {
			margin: 0 30upx 0 13upx;
		}

		.btn {
			background: #19A967;
			color: #fff;
			width: 130upx;
			height: 54upx;
			line-height: 54upx;
			text-align: center;
			color: #fff;
			font-size: 24upx;

			image {
				width: 22upx;
				margin-right: 10upx;
			}
		}
	}
</style>
