<template>
	<view class="shopinfo card">
		<view class="flex align-center">
			<view class="imgbox">
				<image src="../static/demo/2.png" mode="aspectFill"></image>
			</view>
			<view class="flex-sub">
				<view class="flex justify-between align-center">
					<span class="tag">自营</span>
					<view class="name flex-sub">
						小王的店铺
					</view>
					<view class="btn">进入店铺</view>
				</view>
				<view class="margin-top-xs margin-bottom-xs">销量：1231</view>
				<view>
					<tui-rate :current="index" :size="14" active='#fc743c'></tui-rate>
					<text class="num" :style="{color:index==0?'#c9c9c9':'#fc743c'}">{{index?index+'.0':'暂无评价'}}</text>
				</view>
			</view>

		</view>
		<view class="goodslist flex margin-top-sm">
			<view class="goods-item">
				<image src="../static/demo/1.png" mode="widthFix"></image>
				<text>￥16.8/扎</text>
			</view>
			<view class="goods-item">
				<image src="../static/demo/1.png" mode="widthFix"></image>
				<text>￥16.8/扎</text>
			</view>
			<view class="goods-item">
				<image src="../static/demo/1.png" mode="widthFix"></image>
				<text>￥16.8/扎</text>
			</view>
			<view class="goods-item">
				<image src="../static/demo/1.png" mode="widthFix"></image>
				<text>￥16.8/扎</text>
			</view>
		</view>
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
		}
	}
</script>

<style scoped lang="scss">
	.shopinfo {
		background: #fff;
		font-size: 24upx;
		color: #8d8d8d;

		&.card {
			border-radius: 30upx;
			border-top: none;
			padding: 35upx 20upx;

		}

		.imgbox {
			height: 130upx;
			margin-right: 50upx;
			width: 130upx;

			image {
				display: block;
				width: 100%;
				height: 100%;
				border-radius: 100%;
			}
		}

		.name {
			color: #000;
			font-size: 30upx;
		}

		.tag {
			color: #fff;
			background: #e60012;
			line-height: 25upx;
			height: 25upx;
			display: inline-block;
			padding: 0 10upx;
			border-radius: 5upx;
			font-size: 16upx;
			margin-right: 20upx;
		}

		.btn {
			color: #fff;
			font-size: 26upx;
			width: 150upx;
			line-height: 60upx;
			border-radius: 15upx;
			text-align: center;
			background-image: linear-gradient(90deg, #fe8c2d, #fe5504);
		}

		.num {
			font-size: 26upx;
			color: #c9c9c9;
			margin-left: 10upx;
		}

		.goodslist {
			padding-right: 50upx;
			position: relative;
			text-align: center;

			&:before {
				position: absolute;
				top: 0;
				right: 10upx;
				bottom: 0;
				display: block;
				margin: auto;
				width: 30upx;
				height: 30upx;
				color: #8799a3;
				content: "\e6a3";
				text-align: center;
				font-size: 34upx;
				font-family: cuIcon;
				line-height: 30upx
			}

			.goods-item {
				color: #e60012;
				font-size: 22upx;
				width: 22%;

				image {
					width: 100%;
				}

				&+.goods-item {
					margin-left: 4%;
				}
			}
		}
	}
</style>
