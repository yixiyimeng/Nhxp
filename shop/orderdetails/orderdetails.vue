<template>
	<view class="pageview flex flex-direction">
		<view class="topbar bg-white">
			<view class="flex justify-between align-center">
				<text class="num">货位号：001</text>
				<view class="btn">确认配送</view>
			</view>
			<view class="flex justify-between bg-white">
				<view>
					<text>购买商：</text>
					<text class="text-black">方德玫瑰</text>
				</view>
				<view>
					<text>下单时间：</text>
					<text class="text-black">2020-03-01</text>
				</view>
			</view>
		</view>
		<view class="list flex-sub">
			<view class="goods-item">
				<view class="flex justify-between">
					<text class="name">玫瑰类——戴安娜</text>
					<view class="price">
						<text>x</text>
						<text>30</text>
					</view>
				</view>
				<view class="flex align-center margin-top-sm">
					<view class="imgbox">
						<image src="/static/demo/1.png" mode="aspectFill"></image>
					</view>
					<view class="flex-sub">
						<view class="goodsname">戴安娜玫瑰</view>
						<view class="goodsnum">
							<text>库存:489</text>
							<text>销量:54</text>
						</view>
						<view class="goodsprice"><text class="num">￥19.8</text>/扎</view>
					</view>
				</view>
				<div class="goodstag grid col-3 margin-top-sm">
					<view>等级:B级</view>
					<view>枝长:80CM</view>
					<view>产地:云南昆明</view>
					<view>优点:花头漂亮</view>
					<view>瑕疵:刺多</view>
					<view>成熟度:中熟</view>
				</div>
			</view>
			<view class="goods-item">
				<view class="flex justify-between">
					<text class="name">玫瑰类——戴安娜</text>
					<view class="price">
						<text>x</text>
						<text>30</text>
					</view>
				</view>
				<view class="flex align-center margin-top-sm">
					<view class="imgbox">
						<image src="/static/demo/1.png" mode="aspectFill"></image>
					</view>
					<view class="flex-sub">
						<view class="goodsname">戴安娜玫瑰</view>
						<view class="goodsnum">
							<text>库存:489</text>
							<text>销量:54</text>
						</view>
						<view class="goodsprice"><text class="num">￥19.8</text>/扎</view>
					</view>
				</view>
				<div class="goodstag grid col-3 margin-top-sm">
					<view>等级:B级</view>
					<view>枝长:80CM</view>
					<view>产地:云南昆明</view>
					<view>优点:花头漂亮</view>
					<view>瑕疵:刺多</view>
					<view>成熟度:中熟</view>
				</div>
			</view>
			<view class="goods-item">
				<view class="flex justify-between">
					<text class="name">玫瑰类——戴安娜</text>
					<view class="price">
						<text>x</text>
						<text>30</text>
					</view>
				</view>
				<view class="flex align-center margin-top-sm">
					<view class="imgbox">
						<image src="/static/demo/1.png" mode="aspectFill"></image>
					</view>
					<view class="flex-sub">
						<view class="goodsname">戴安娜玫瑰</view>
						<view class="goodsnum">
							<text>库存:489</text>
							<text>销量:54</text>
						</view>
						<view class="goodsprice"><text class="num">￥19.8</text>/扎</view>
					</view>
				</view>
				<div class="goodstag grid col-3 margin-top-sm">
					<view>等级:B级</view>
					<view>枝长:80CM</view>
					<view>产地:云南昆明</view>
					<view>优点:花头漂亮</view>
					<view>瑕疵:刺多</view>
					<view>成熟度:中熟</view>
				</div>
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
	page,.pageview{
		height: 100%;
		width: 100%;
	}
	.topbar {
		color: #7F7F7F;
		padding: 30upx;
		font-size: 28upx;

		.text-black {
			color: #2E2E2E;
		}

		&>view {
			margin-top: 28upx;
		}

		.num {
			font-size: 32upx;
			color: #FD3C3E;
		}

		.btn {
			color: #fff;
			background: #19A967;
			width: 160upx;
			height: 60upx;
			border-radius: 8upx;
			text-align: center;
			line-height: 60upx;
		}
	}

	.list {
		border-top: 12upx solid #F8F8F8;
		overflow: auto;
		padding-bottom: 20upx;
		-webkit-overflow-scrolling: touch;

		.goods-item {
			margin: 20upx 30upx 0;
			border-radius: 8upx;
			padding: 25upx;
			box-shadow: 0px 4upx 16upx 0px rgba(213, 213, 213, 1);

			.name {
				color: #A0A0A0;
				font-size: 28upx;
			}

			.price {
				color: #FD3C3E;
				font-size: 32upx;
			}

			.imgbox {
				width: 140upx;
				height: 140upx;
				border-radius: 10upx;
				margin-right: 24upx;
				overflow: hidden;

				image {
					height: 100%;
					width: 100%;
				}
			}

			.goodsname {
				color: #232323;
				font-size: 32upx;
			}

			.goodsnum {
				color: #9F9F9F;
				font-size: 26upx;
				margin: 20upx 0;
			}

			.goodsprice {
				font-size: 24upx;
				color: #C0C0C0;

				.num {
					color: #FD3C3E;
				}
			}

		}
	}

	.goodstag {
		background: #F4F4F4;
		padding: 25upx 10upx;
		border-radius: 8upx;
		color: #515151;
		font-size: 24upx;

		view {
			padding: 5upx 0;
		}
	}
</style>
