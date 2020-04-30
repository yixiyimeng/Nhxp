<template>
	<view class="pageview flex flex-direction">
		<view class="main flex-sub orderinfo">
			<view class="card bg-white">
				<!-- <view class="noaddr flex align-center justify-center">+ 新增收货地址</view> -->
				<view class="addrbox flex align-center">
					<image src="/static/icon15.png" mode="widthFix" class="addr"></image>
					<view class="flex-sub">
						<view class="">
							<text class="name">王小姐</text>
							<text>13888145285</text>
						</view>
						<view class="margin-top-sm">云南省昆明市五华区1111号</view>
					</view>
					<image src="/static/icon18.png" mode="widthFix" class="arrow"></image>
				</view>
			</view>
			<view class="card bg-white margin-top shop">
				<view class="shop-hd flex align-center">
					<image src="../../static/demo/2.png" mode="widthFix"></image>
					<text>小碗的店铺</text>
				</view>
				<view class="shop-bd">
					<view class="goods-item flex align-center">
						<image src="../../static/demo/img.jpg" mode=""></image>
						<view class="flex-sub">
							<view class="flex justify-between align-center">
								<view class="name">多头玫瑰</view>
								<view class="text-red">x<text class="num">2</text></view>
							</view>
							<view class="tag">B 10支/扎 橙色</view>
							<view class="price text-red">￥15.80 </view>
						</view>
					</view>
					<view class="goods-item flex align-center">
						<image src="../../static/demo/img.jpg" mode=""></image>
						<view class="flex-sub">
							<view class="flex justify-between align-center">
								<view class="name">多头玫瑰</view>
								<view class="text-red">x<text class="num">2</text></view>
							</view>
							<view class="tag">B 10支/扎 橙色</view>
							<view class="price text-red">￥15.80 </view>
						</view>
					</view>
					<view class="group-row flex align-center margin-top-lg">
						<view class="title">订单备注</view>
						<input type="text" placeholder="选填，颜色、开放度" class="flex-sub">
					</view>
				</view>
			</view>
			<view class="card bg-white margin-top shop">
				<view class="shop-hd flex align-center">
					<image src="../../static/demo/2.png" mode="widthFix"></image>
					<text>小碗的店铺</text>
				</view>
				<view class="shop-bd">
					<view class="goods-item flex align-center">
						<image src="../../static/demo/img.jpg" mode=""></image>
						<view class="flex-sub">
							<view class="flex justify-between align-center">
								<view class="name">多头玫瑰</view>
								<view class="text-red">x<text class="num">2</text></view>
							</view>
							<view class="tag">B 10支/扎 橙色</view>
							<view class="price text-red">￥15.80 </view>
						</view>
					</view>
					<view class="goods-item flex align-center">
						<image src="../../static/demo/img.jpg" mode=""></image>
						<view class="flex-sub">
							<view class="flex justify-between align-center">
								<view class="name">多头玫瑰</view>
								<view class="text-red">x<text class="num">2</text></view>
							</view>
							<view class="tag">B 10支/扎 橙色</view>
							<view class="price text-red">￥15.80 </view>
						</view>
					</view>
					<view class="group-row flex align-center margin-top-lg">
						<view class="title">订单备注</view>
						<input type="text" placeholder="选填，颜色、开放度" class="flex-sub">
					</view>
				</view>
				<view class="shop-ft flex align-center justify-center">
					<text>显示全部</text>
					<text class="cuIcon-unfold"></text>
				</view>
			</view>
			<view class="card bg-white margin-top">
				<view class="group-row flex align-center">
					<view class="title">订单备注</view>
					<input type="text" placeholder="选填，颜色、开放度" class="flex-sub">
				</view>

			</view>
			<view class="card bg-white margin-top">
				<view class="group-row flex align-center justify-between">
					<view class="title">配送方式</view>
					<view class="picker">
						<text>快递运输</text>
						<text class="cuIcon-right"></text>
					</view>
				</view>
			</view>
			<view class="card bg-white margin-top">
				<view class="group-row flex align-center justify-between">
					<view class="title">支付方式</view>
					<picker mode="selector" :range="paywaylist" @change="PickerChange" :value="payway" range-key="name">
						<view class="picker">
							<text>{{payway==0?'微信支付':'余额支付'}}</text>
							<text class="cuIcon-right"></text>
						</view>
					</picker>
				</view>
			</view>
			<view class="card bg-white margin-top">
				<view class="group-row  flex align-center justify-between">
					<view class="title">花款小计</view>
					<text class="text-gray">￥0.00</text>
				</view>
				<view class="group-row margin-top">
					<view class="flex align-center justify-between">
						<view class="title">包装费</view>
						<text class="text-gray">￥0.00</text>
					</view>
					<view class="tag">费用由运输方多退少补</view>
				</view>
				<view class="group-row margin-top">
					<view class="flex align-center justify-between">
						<view class="title">运输费</view>
						<text class="text-gray">￥0.00</text>
					</view>
					<view class="tag">费用由运输方多退少补</view>
				</view>
				<view class="group-row margin-top">
					<view class="flex align-center justify-between">
						<view class="title">服务费</view>
						<text class="text-gray">￥0.00</text>
					</view>
					<view class="tag">费用由运输方多退少补</view>
				</view>
			</view>
		</view>
		<view class="footerbar bg-white flex align-center">
			<view class="flex-sub text-right">合计：<text class="text-red">￥15.8</text></view>
			<view class="btn">立即支付</view>
		</view>
		<view class="cu-modal bottom-modal" :class="showfastmailway?'show':''">
			<view class="cu-dialog">
				<view class="fastmailway bg-white">
					<view class="tip">请从以下<text class="text-red">5</text>种物流方式中选择，运费遵循多退少补的原则</view>
					<radio-group class="block" @change="RadioChange">
						<view>
							<view class="fastmail-item">
								<view class="flex align-center">
									<view class="name">快递运输</view>
									<view class="flex-sub">
										<text class="text-red">*</text>
										<text>正常情况下，2天左右到达</text>
									</view>
									<radio value="" class="orange" />
								</view>
								<view class="tag">服务说明：多数地区均可选择该运输方式，配送到店。</view>
							</view>
							<view class="fastmail-item">
								<view class="flex align-center">
									<view class="name">快递运输</view>
									<view class="flex-sub">
										<text class="text-red">*</text>
										<text>正常情况下，2天左右到达</text>
									</view>
									<radio value="" class="orange" />
								</view>
								<view class="tag">服务说明：多数地区均可选择该运输方式，配送到店。</view>
							</view>
						</view>
					</radio-group>
				</view>
				<view class="modalbtn">确定</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				paywaylist: [{
					'name': '微信支付',
					id: 0
				}, {
					'name': '余额支付',
					id: 1
				}],
				payway: 0,
				showfastmailway: false //打开快递选择
			};
		},
		methods: {
			PickerChange(e) {
				this.payway = e.value;
			}
		}
	}
</script>

<style lang="scss">
	page,
	.pageview {
		height: 100%;
		background: #ededed;
		overflow: hidden;
		width: 100%;
		color: #000;
		font-size: 26upx;

		.main {
			overflow: auto;
			padding: 30upx 25upx;
			-webkit-overflow-scrolling: touch;

			.card {
				border-radius: 30upx;
				padding: 40upx 30upx;

				.noaddr {
					height: 70upx;
					font-weight: blod;
					color: #000;
				}

				.group-row {
					.title {
						width: 4em;
						margin-right: 40upx;
						font-weight: bold;
						color: #000;
					}

					input {
						background: #f2f3f7;
						border-radius: 10upx;
						height: 50upx;
						line-height: 50upx;
						padding-left: 30upx;
						font-size: 20upx;
					}

					.picker {
						font-size: 22upx;
						color: #a4a4a4;

						text {
							vertical-align: middle;
						}

						.cuIcon-right {
							font-size: 40upx;
							color: #474747;
							margin-left: 20upx;
						}
					}

					.text-gray {
						font-size: 22upx;
						color: #a4a4a4;
					}

					.tag {
						padding-top: 20upx;
						color: #8f8f8f;
						font-size: 20upx;
					}
				}

			}

			.shop {
				padding: 0;

				.shop-hd {
					height: 74upx;
					padding-left: 33upx;
					font-size: 22upx;
					border-bottom: 1px solid #eee;
					font-weight: blod;

					image {
						height: 45upx;
						width: 45upx;
						border-radius: 100%;
						margin-right: 20upx;
					}
				}

				.shop-bd {
					padding: 30upx;
					color: #000;
				}

				.shop-ft {
					height: 65upx;
					color: #000;
					font-size: 24upx;
					border-top: 1px solid #eee;
					font-weight: blod;

					.cuIcon-unfold {
						color: #9c9c9c;
						margin-left: 15upx;
					}
				}

				.goods-item {
					image {
						width: 124upx;
						height: 124upx;
						margin-right: 30upx;
					}

					&+.goods-item {
						margin-top: 30upx;
					}

					.name {
						font-weight: blod;
						font-size: 30upx;
					}

					.num {
						font-weight: bloder;
						font-size: 28upx;
						margin-right: 100upx;
					}

					.tag {
						color: #b3b6be;
						font-size: 20upx;
						margin: 15upx 0 20upx;
					}

					.price {
						font-size: 28upx;
						font-weight: bloder;
					}
				}
			}
		}

		.footerbar {
			height: 109upx;
			position: relative;
			z-index: 99;
			box-shadow: 0 -5upx 5upx rgba(0, 0, 0, .1);
			padding: 0 25upx;

			.btn {
				font-size: 30upx;
				color: #fff;
				background-image: linear-gradient(90deg, #fb9549, #fc733b);
				height: 80upx;
				width: 150upx;
				border-radius: 10upx;
				text-align: center;
				line-height: 80upx;
				margin-left: 30upx;
			}
		}

		.fastmail-item {
			color: #a1a1a1;
			font-size: 20upx;
			text-align: left;

			&+.fastmail-item {
				margin-top: 20upx;
			}

			.name {
				color: #fff;
				background-image: linear-gradient(90deg, #fb9549, #fc733b);
				border-radius: 10upx;
				text-align: center;
				line-height: 50upx;
				width: 127upx;
				font-size: 22upx;
				margin-right: 24upx;
			}

			.tag {
				background: #f2f3f7;
				padding: 20upx 35upx;
				font-size: 20upx;
				color: #747474;
				line-height: 48upx;
				margin-top: 10upx;
				border-radius: 10upx;
			}

			radio {
				transform: scale(.7);
			}
		}

		.cu-dialog {
			.fastmailway {
				padding: 37upx 60upx 30upx;
				text-align: left;

				.tip {
					color: #626262;
					font-size: 22upx;
					margin-bottom: 20upx;
				}
			}
		}


	}
</style>
