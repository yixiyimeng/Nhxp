<template>
	<view class="card">
		<div class="tjtag">{{goodsinfo.tjtag==2?'平台推荐':'今日特惠'}}</div>
		<div class="flex bg-white">
			<div>
				<div class="imgbox">
					<image src="/static/demo/img.jpg" mode="widthFix"></image>
				</div>
				<view class="margin-top-xs">共<text class="shopnum">1</text>家供应商报价</view>
			</div>
			<div class="flex-sub">
				<div class="flex justify-between">
					<text class="name">多头玫瑰</text>
					<text class="oldprice">平均价￥15.80</text>
				</div>
				<div class="flex justify-between align-center padding-top-sm padding-bottom-sm">
					<div>颜色：红色</div>
					<div class="price">￥15.80</div>
				</div>
				<div class="flex justify-between align-end solid-top padding-top">
					<div class="num">
						<div>库存：123</div>
						<div class="margin-top-sm">销量：2354</div>
					</div>
					<view class="buybtn" :class="{'open':isOpen}" @tap="tapOpen">
						<text>选 购</text>
						<image src="/static/icon26.png" mode="widthFix" v-if="!isOpen"></image>
						<image src="/static/icon27.png" mode="widthFix" v-else></image>
					</view>
				</div>
			</div>
		</div>
		<template v-if="isOpen">
			<div class="maillist margin-top" :class="{active:isOpenitem}">
				<goods type="1" v-for="(item, index) in 2" :key="index"></goods>
			</div>
		</template>
	</view>
</template>

<script>
	import goods from "./goods.vue"
	export default {
		data() {
			return {
				isOpen: false,
				isOpenitem: false
			};
		},
		components: {
			goods
		},
		props: {
			goodsinfo: {
				type: Object,
				default: {}
			},
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
		},
		methods: {
			tapOpen() {
				if (this.isOpen) {
					this.isOpenitem = false;
					this.$nextTick(() => {
						this.isOpen = false;
					})
				} else {
					this.isOpen = true;
					this.$nextTick(() => {
						this.isOpenitem = true
					})
				}
			},
		}
	}
</script>

<style lang="scss">
	.card {
		border-radius: 30upx;
		position: relative;
		overflow: hidden;
		padding: 35upx 20upx;
		background: #fff;
		margin: 0 20upx 20upx;
		color: #000;

		.shopnum {
			color: #e53f3f;
			font-size: 30upx;
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

		.oldprice {
			color: #b5b8c1;
			font-size: 24upx;
			text-decoration: line-through;

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
		}

		.price {
			color: #e03d3e;
			font-size: 38upx;
			font-weight: bold;
		}

		.buybtn {
			color: #fc733b;
			font-size: 30upx;
			height: 60upx;
			width: 150upx;
			border-radius: 16upx;
			border: 2upx solid #fc733b;
			text-align: center;
			line-height: 60upx;

			text,
			image {
				vertical-align: middle;
			}

			image {
				margin-left: 14upx;
				width: 18upx;
			}

			&.open {
				color: #fff;
				background: #ff0000;
				border: 2upx solid #ff0000;
			}
		}

	}

	.goodsinfo+.goodsinfo {
		margin-top: 20upx;
	}
</style>
