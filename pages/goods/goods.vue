<template>
	<view class="pageview flex flex-direction">
		<view class="flex-sub main">
			<view class="slide bg-white">
				<swiper class="swiper" :interval="8000" :duration="1000" indicator-color="#d2d2d2" indicator-active-color="#fc743b">
					<swiper-item v-for="(item, itemIndex) in imglist" :key="itemIndex">
						<image class="slide-image" :src="item.img" mode="widthFix" />
					</swiper-item>
				</swiper>
			</view>
			<view class="goodsinfo bg-white">
				<div class="name flex justify-between align-center">
					<text>多头玫瑰</text>
					<view>
						<view class="fav"></view>
						<view class="share"></view>
					</view>
				</div>
				<div class="flex justify-between margin-top align-center">
					<div class="shopinfo">
						<span class="tag">自营</span>
						<span class='favstate'>关注过的店</span>
						<span>小王的店铺呀呀呀</span>
						<span class="link">进店 ></span>
					</div>
					<div class="price">￥15.80</div>
				</div>
				<div class="num margin-top">
					<text>库存：123</text>
					<text class="margin-left-lg">销量：2354</text>
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
			<view class="bg-white margin-top-xs cu-bar">
				<view class="action">
					商品评价（0）
				</view>
				<view class="action">暂无产品评价 ></view>
			</view>
			<view class="bg-white margin-top-xs cu-bar">
				<view class="action">
					商品评价（2345）
				</view>
				<view class="action more">查看全部 ></view>
			</view>
			<view class="bg-white replylist">
				<cmt-reply v-for="(item,index) in 2" :key="index"></cmt-reply>
			</view>
			<view class="bg-white margin-top-xs cu-bar">
				<view class="action">
					购前须知
				</view>
			</view>
			<view class="needknow bg-white">
				<p>在您下订单购买商品时，请你仔细确认所购商品的名称，单位，颜色等，以及收货地址，收货人姓名，电话等信息，如果因为用户填写信息不符造成的货物不能按时到达等后果，本站不承担风险。如果及时发现输入信息错误，可在货物到达前联系客服修改。</p>
				<p>货物到达时，如果配送员联络不到用户或多次联系无人接听或关机，造成货物积压时间太长造成的损失，本站不承担风险</p>
				<p>活动用花，婚庆用花，订单用花等着急用花的用户，如果因物流等其他不可抗拒的因素导致货物不能及时到达或者其他因素，对此造成的损失，本站只负责对鲜花质量问题进行售后，其他损失不予承担。</p>
				<p>鲜花属于鲜活产品，农副产品，下单并成功发货后不可以退换货，因各种原因用户拒收货物的，本站不予退款。</p>
			</view>
		</view>
		<view class="ftbar flex align-center justify-between">
			<view class="flex align-center">
				<navigator url="">
					<image src="/static/icon28.png" mode="widthFix"></image>
					<text>首页</text>
				</navigator>
				<navigator url="">
					<image src="/static/icon29.png" mode="widthFix"></image>
					<text>采购单</text>
				</navigator>
				<navigator url="">
					<image src="/static/icon20.png" mode="widthFix"></image>
					<text>客服</text>
				</navigator>
			</view>
			<view class="btn">去下单</view>
		</view>
	</view>
</template>

<script>
	import cmtReply from "@/components/cmt-reply"
	export default {
		data() {
			return {
				imglist: [{
					img: '/static/demo/img1.jpg'
				}, {
					img: '/static/demo/img1.jpg'
				}]
			};
		},
		components: {
			cmtReply
		}
	}
</script>
<style>
	page,
	.pageview {
		height: 100%;
		width: 100%;
		overflow: hidden;
	}
</style>
<style lang="scss" scoped>
	.pageview {
		background: #eee;

		.main {
			overflow: auto;
			-webkit-overflow-scrolling: touch;
		}
	}

	.swiper {
		width: 100vw;
		height: 100vw;
	}

	.goodsinfo {
		background: #fff;
		color: #000;
		position: relative;
		overflow: hidden;
		padding: 30upx 65upx;

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

		}

		.info {
			background: #f2f3f7;
			margin: 30upx -20upx 0;
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
			background-image: url(../../static/icon13.png);
			margin-right: 30upx;
		}

		.share {
			background-image: url(../../static/icon14.png);
		}
	}

	.replylist {
		padding: 20upx 90upx;
	}

	.cu-bar {
		.more {
			color: #fc723b;
			font-size: 26upx;
		}

		.action:first-child {
			margin-left: 65upx;
			font-weight: bolder;
		}

		.action:last-child {
			margin-right: 65upx;
		}
	}

	.needknow {
		color: #929292;
		font-size: 20upx;
		padding: 0 90upx 30upx;
		line-height: 36upx;

		p {
			position: relative;
			padding-left: 25upx;

			&:before {
				width: 12upx;
				height: 12upx;
				display: block;
				content: '';
				background: #fc723b;
				border-radius: 100%;
				position: absolute;
				left: 0;
				top: 10upx;
			}

			&+p {
				margin-top: 20upx;
			}
		}
	}

	.ftbar {
		background: #fff;
		height: 110upx;
		border-top: 1px solid #f0f0f0;

		.btn {
			color: #fff;
			font-size: 30upx;
			width: 150upx;
			line-height: 80upx;
			border-radius: 15upx;
			text-align: center;
			background-image: linear-gradient(90deg, #fe8c2d, #fe5504);
			margin-right: 40upx;
		}

		navigator {
			color: #6b6b6b;
			font-size: 22upx;
			margin: 0 50upx;
			text-align: center;

			image {
				width: 37upx;
				display: block;
				margin: 0 auto 10upx;
			}
		}
	}
</style>
