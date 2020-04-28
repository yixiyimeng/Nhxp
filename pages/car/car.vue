<template>
	<view class="pageview">
		<view class="topnav bg-white flex align-center justify-center">
			<span class="topnav-item active">全部产品</span>
		</view>
		<span class="del">删除</span>
		<view class="list">
			<view class="card shop-item">
				<view class="shopinfo flex align-center">
					<label class="checkbox">
						<checkbox class="round orange"></checkbox>
					</label>
					<navigator url="#">
						<image src="/static/demo/2.png" mode="widthFix"></image>
						<text>小王的店 ></text>
					</navigator>
				</view>
				<view class="goodslist">
					<view class="goods-item flex align-center">
						<label class="checkbox">
							<checkbox class="round orange"></checkbox>
						</label>
						<image src="../../static/demo/img.jpg" mode="widthFix"></image>
						<view class="flex-sub">
							<view class="name">
								多头玫瑰
							</view>
							<view class="tag flex align-center">
								等级：A 单位：20支/扎 长度：60CM
							</view>
							<view class="flex justify-between margin-right-sm">
								<text class="price">￥15.80</text>
								<numberbox :value='num' @change="changeNum"></numberbox>
							</view>
						</view>
					</view>
					<view class="goods-item flex align-center">
						<label class="checkbox">
							<checkbox class="round orange"></checkbox>
						</label>
						<image src="../../static/demo/img.jpg" mode="widthFix"></image>
						<view class="flex-sub">
							<view class="name">
								多头玫瑰
							</view>
							<view class="tag flex align-center">
								等级：A 单位：20支/扎 长度：60CM
							</view>
							<view class="flex justify-between margin-right-sm">
								<text class="price">￥15.80</text>
								<numberbox :value='num' @change="changeNum"></numberbox>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="card shop-item">
				<view class="shopinfo flex align-center">
					<label class="checkbox">
						<checkbox class="round orange"></checkbox>
					</label>
					<navigator url="#">
						<image src="/static/demo/2.png" mode="widthFix"></image>
						<text>小王的店 ></text>
					</navigator>
				</view>
				<view class="goodslist">
					<view class="goods-item flex align-center">
						<label class="checkbox">
							<checkbox class="round orange"></checkbox>
						</label>
						<image src="../../static/demo/img.jpg" mode="widthFix"></image>
						<view class="flex-sub">
							<view class="name">
								多头玫瑰
							</view>
							<view class="tag flex align-center">
								等级：A 单位：20支/扎 长度：60CM
							</view>
							<view class="flex justify-between margin-right-sm">
								<text class="price">￥15.80</text>
								<numberbox :value='num' @change="changeNum"></numberbox>
							</view>
						</view>
					</view>

				</view>
			</view>
			<view class="card invalid">
				<view class="title flex align-center justify-between">
					<view>失效产品共1件</view>
					<view class="text-orange">清空失效产品</view>
				</view>
				<view class="goodslist">
					<view class="goods-item flex align-center">
						<span class="state">失效</span>
						<image src="../../static/demo/img.jpg" mode="widthFix"></image>
						<view class="flex-sub">
							<view class="name">
								多头玫瑰
							</view>
							<view class="tag flex align-center">
								商品已下架或无库存
							</view>

						</view>
					</view>

				</view>
			</view>
		</view>
		<view class="carbar bg-white">
			<checkbox-group class="block flex justify-between align-center" @change="RadioChange">
				<label class="checkbox flex-sub flex align-center">
					<checkbox class="round orange" :class="allcheck=='allcheck'?'checked':''" :checked="allcheck=='allcheck'?true:false"
					 value="allcheck"></checkbox>
					<text>全选</text>
				</label>
				<view>
					合计：<span class="price">￥15.8</span>
				</view>
				<view class="paybtn">去下单</view>
			</checkbox-group>
		</view>
	</view>
</template>

<script>
	import Numberbox from '@/components/numberbox.vue'
	export default {
		data() {
			return {
				allcheck: null,
				num: 1
			};
		},
		components: {
			Numberbox
		},
		methods: {
			RadioChange(e) {
				this.allcheck = e.detail.value
			},
			changeNum(e) {
				this.num = e.value
			}
		}
	}
</script>

<style lang="scss">
	page,
	.pageview {
		height: 100%;
		width: 100%;
		background: #f0f0f0;
		position: relative;

		.checkbox {
			font-size: 30upx;

			checkbox {
				transform: scale(.7);
				margin-right: 15upx;
			}
		}

		.topnav {
			position: absolute;
			top: 0;
			left: 0;
			width: 100%;
			height: 94upx;
			color: #000;
			font-size: 30upx;

			.topnav-item {
				padding: 15upx 0;
				margin: 0 15upx;
				position: relative;

				&.active {
					color: #fc723a;

					&:after {
						content: '';
						display: block;
						height: 1px;
						width: 65upx;
						background: #fc723a;
						position: absolute;
						bottom: 0;
						left: 50%;
						transform: translateX(-50%);
					}
				}
			}
		}

		.carbar {
			position: absolute;
			bottom: 0;
			left: 0;
			width: 100%;
			height: 110upx;
			font-size: 26upx;
			padding: 0 30upx;

			.block {
				width: 100%;
				height: 110upx;
			}

			.price {
				color: #e03d3e;
			}

			.paybtn {
				margin-left: 30upx;
				font-size: 30upx;
				text-align: center;
				line-height: 80upx;
				width: 150upx;
				border-radius: 20upx;
				color: #fff;
				background-image: linear-gradient(90deg, #fa9148, #fc773d);
			}


		}

		.list {
			position: absolute;
			top: 94upx;
			left: 0;
			width: 100%;
			bottom: 110upx;
			overflow: auto;
			padding: 0 25upx 30upx;

			.card {
				background: #fff;
				border-radius: 20upx;
				margin-top: 30upx;

				.shopinfo {
					border-bottom: 1px solid #e5e5e5;
					height: 90upx;
					font-size: 28upx;
					font-weight: blod;
					color: #000;

					image {
						display: inline-block;
						width: 65upx;
						height: 65upx;
						border-radius: 100%;
						vertical-align: middle;
						margin-right: 20upx;
					}

					text {
						vertical-align: middle;
					}
				}

				.goodslist {
					.goods-item {
						padding: 15upx 0;

						&>image {
							width: 191upx;
							height: 191upx;
							margin-right: 30upx;
						}

						.name {
							font-size: 30upx;
							font-weight: bold;
						}

						.tag {
							color: #b3b6be;
							font-size: 22upx;
							height: 80upx;
							border-bottom: 1px solid #f2f3f7;
							margin-bottom: 20upx;
						}

						.price {
							color: #e03d3e;
							font-size: 38upx;
							font-weight: bolder;
						}
					}
				}

				&.invalid {
					.title {
						height: 90upx;
						font-size: 26upx;
						border-bottom: 1px solid #e5e5e5;
						padding: 0 30upx;
					}

					.goodslist {
						.goods-item {
							.state {
								color: #fff;
								font-size: 22upx;
								background: #959595;
								width: 65upx;
								height: 35upx;
								line-height: 35upx;
								text-align: center;
								border-radius: 10upx;
								margin-left: 5upx;
							}
							.tag{
								border-bottom: none;
							}
						}
					}
				}
			}
		}
	}
</style>
