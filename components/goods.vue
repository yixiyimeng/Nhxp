<template>
	<view class="goodsinfo" :class="{card:type==0}">
		<div class="tjtag" v-if="type==0">{{goodsinfo.tjtag==2?'平台推荐':'今日特惠'}}</div>
		<div class="flex">
			<div class="imgbox">
				<image src="/static/demo/img.jpg" mode="widthFix"></image>
			</div>
			<div class="flex-sub">
				<div class="name flex justify-between">
					<text>多头玫瑰</text>
					<view>
						<view class="fav"></view>
						<view class="share"></view>
					</view>
				</div>
				<div class="num">
					<text>库存：123</text>
					<text>销量：2354</text>
				</div>
				<div class="price">￥15.80</div>
			</div>
		</div>
		<div class="shopinfo">
			<span class="tag">{{goodsinfo.state|filtertag}}</span>
			<span class='favstate'>关注过的店</span>
			<span>小王的店铺呀呀呀</span>
			<span class="link">进店 ></span>
			<span class="btn">加入采购单</span>
		</div>
		<div class="info flex flex-wrap">
			<view class="text-cut">等级：A</view>
			<view class="text-cut">单位：20支/扎</view>
			<view class="text-cut">长度：60-70cm</view>
			<view class="text-cut">成熟度：中熟</view>
			<view class="text-cut">优点：枝条粗、花头大</view>
			<view class="text-cut">缺点：刺多</view>
		</div>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		props: {
			goodsinfo: {
				type: String,
				default: {}
			},
			type: {
				type: [String, Number],
				default: 0
			}
		},
		filters: {
			filtertag(value) {
				if (value == 1) {
					return '自营'
				} else if (value == 2) {
					return '品牌'
				} else {
					return '基地'
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	.goodsinfo {
		background: #fff;
		color: #000;
		position: relative;
		overflow: hidden;
		border-top: 1px solid #ededed;
		padding: 30upx 0;

		&.card {
			border-radius: 30upx;
			border-top: none;
			padding: 35upx 20upx;

		}

		&:not(last-child) {
			padding-bottom: 0;
		}

		.tjtag {
			position: absolute;
			left: 30upx;
			top: 0;
			height: 58upx;
			width: 58upx;
			border-radius: 0 20upx 0 20upx;
			color: #fff;
			font-size: 16upx;
			padding: 10upx;
			background: #e60012;
			z-index: 99;
			text-align: center;

			&.tjtag1 {
				background: #917bdd;
			}
		}

		.name {
			font-size: 30upx;
			font-weight: bold;
		}

		.imgbox {
			width: 191upx;
			height: 191upx;
			margin-right: 35upx;

			image {
				height: 100%;
				width: 100%;
				display: block;
			}
		}

		.num {
			color: #b3b6be;
			font-size: 24upx;
			padding: 20upx 0 30upx;
			border-bottom: 1px solid #f2f3f7;
		}

		.price {
			color: #e03d3e;
			font-size: 38upx;
			font-weight: bold;
		}

		.shopinfo {
			font-size: 20upx;
			color: #666;
			margin-top: 10upx;
			position: relative;

			.link {
				color: #000;
				margin-left: 12upx;
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
				margin-right: 10upx;
			}

			.favstate {
				color: #fb8442;
			}

			.btn {
				position: absolute;
				bottom: 0;
				right: 0;
				color: #fff;
				font-size: 24upx;
				width: 150upx;
				line-height: 60upx;
				border-radius: 15upx;
				text-align: center;
				background-image: linear-gradient(90deg, #fe8c2d, #fe5504);
			}
		}

		.info {
			background: #f2f3f7;
			margin-top: 30upx;

			padding: 5upx 20upx;

			&>view {
				width: 30%;
				padding: 10upx 0;

				&:nth-child(3n+2) {
					width: 40%;
				}
			}
		}

		.fav,
		.share {
			height: 40upx;
			width: 40upx;
			background: no-repeat center center;
			background-size: contain;
			display: inline-block;
		}

		.fav {
			background-image: url(../static/icon13.png);
			margin-right: 30upx;
		}

		.share {
			background-image: url(../static/icon14.png);
		}
	}
</style>
