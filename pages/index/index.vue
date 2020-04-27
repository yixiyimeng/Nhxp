<template>
	<view class="view-page">
		<mescroll-body ref="mescrollRef" @init="mescrollInit" @down="downCallback" @up="upCallback" @scroll="scroll"
		 @topclick="topClick">
			<view class="bg-white">
				<!-- banner -->
				<view class="slide">
					<swiper class="swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" indicator-color="#fff"
					 indicator-active-color="#ff5454">
						<swiper-item v-for="(item, itemIndex) in imglist" :key="itemIndex">
							<image class="slide-image" :src="item.img" mode="widthFix" />
						</swiper-item>
					</swiper>
				</view>
				<view class="tag flex align-center justify-center">
					<span><text class="icon icon1"></text><text>基地直供</text></span>
					<span><text class="icon icon2"></text><text>花比三家</text></span>
					<span><text class="icon icon3"></text><text>用心服务</text></span>
					<span><text class="icon icon4"></text><text>售后保证</text></span>
				</view>
				<!-- menu -->
				<view class="cu-list grid col-4 no-border">
					<view class="cu-item" v-for="(item,index) in cuIconList" :key="index">
						<view class="imgbox">
							<image :src="item.img" mode="widthFix"></image>
						</view>

						<text>{{item.name}}</text>
					</view>
				</view>
				<!-- 公告 -->
				<view class="notice flex align-center">
					<view class="title">商城头条</view>
					<view class="line"></view>
					<view class="msg flex-sub text-cut">{{msg}}</view>
				</view>
			</view>
			<!-- tab -->
			<view class="flex tabnav">
				<view class="tab-item flex-sub" :class="{active:tabindex==0}">
					<view class="title">今日特惠</view>
					<view class="tag">性价比高</view>
				</view>
				<view class="line"></view>
				<view class="tab-item flex-sub" :class="{active:tabindex==1}">
					<view class="title">今日特惠</view>
					<view class="tag">性价比高</view>
				</view>
				<view class="line"></view>
				<view class="tab-item flex-sub" :class="{active:tabindex==2}">
					<view class="title">今日特惠</view>
					<view class="tag">性价比高</view>
				</view>
				<view class="line"></view>
				<view class="tab-item flex-sub" :class="{active:tabindex==3}">
					<view class="title">今日特惠</view>
					<view class="tag">性价比高</view>
				</view>
			</view>
			<view class="list">
				<goods></goods>
			</view>

		</mescroll-body>
	</view>
</template>

<script>
	import MescrollMixin from "@/components/mescroll-uni/mescroll-mixins.js";
	import goods from "@/components/goods"
	export default {
		data() {
			return {
				isShowSticky: false,
				navTop: null,
				msg: '下单后当天发货，时效问题不保证，请谨慎下单',
				imglist: [{
					img: '/static/demo/banner2.jpg'
				}],
				cuIconList: [{
					img: '/static/icon5.png',
					name: '全部花材',
					url: ''
				}, {
					img: '/static/icon6.png',
					name: '特惠专区',
					url: ''
				}, {
					img: '/static/icon7.png',
					name: '新手指南',
					url: ''
				}, {
					img: '/static/icon8.png',
					name: '运输说明',
					url: ''
				}, {
					img: '/static/icon9.png',
					name: '售后规定'
				}, {
					img: '/static/icon10.png',
					name: '签到'
				}, {
					img: '/static/icon11.png',
					name: '领现金'
				}, {
					img: '/static/icon12.png',
					name: '平台公示'
				}],
				tabindex: 0
			};
		},
		mixins: [MescrollMixin],
		components: {
			goods
		},
		methods: {
			topClick() {
				this.isShowSticky = false
			},
			setNavTop() {
				let view = uni.createSelectorQuery().select('#tabInList');
				view.boundingClientRect(data => {
					this.navTop = data.top // 到屏幕顶部的距离
				}).exec();
			},
		},
		onPageScroll(e) {
			console.log('滚动条位置 = ' + e.scrollTop + ', navTop = ' + this.navTop);
			if (e.scrollTop >= this.navTop) {
				this.isShowSticky = true // 显示悬浮菜单
			} else {
				this.isShowSticky = false // 隐藏悬浮菜单
			}
		}
	};
</script>

<style lang="scss">
	page,
	.view-page {
		height: 100%;
		// overflow: hidden;
		position: relative;
		background: #f0f0f0;
	}
	.tag {
		color: #7f7f7f;
		font-size: 22upx;

		span+span {
			margin-left: 25upx;
		}

		.icon {
			display: inline-block;
			margin-right: 10upx;
			height: 24upx;
			width: 24upx;
			vertical-align: middle;
			background: url(../../static/icon1.png) no-repeat center center;

			&.icon1 {
				background-size: 24upx auto;
			}

			&.icon2 {
				background-image: url(../../static/icon2.png);
				background-size: 19upx auto;
			}

			&.icon3 {
				background-image: url(../../static/icon3.png);
				background-size: 20upx auto;
			}

			&.icon4 {
				background-image: url(../../static/icon4.png);
				background-size: 18upx auto;
			}
		}

		.icon+text {
			vertical-align: middle;
		}

	}

	.grid {
		margin: 30upx auto 10upx;

		.imgbox {
			height: 94upx;
			width: 94upx;
			margin: 0 auto 20upx;

			image {
				height: 94upx;
				width: 94upx;
				display: block;
			}
		}

		.imgbox+text {
			font-size: 22upx;
			color: #000;
			padding-bottom: 16upx;
			margin-top: 0;
		}
	}

	.notice {
		background-image: linear-gradient(45deg, #fe8c2d, #fe5504);
		color: #fff;
		height: 70upx;
		font-size: 20upx;

		.title {
			font-size: 30upx;
			padding-left: 80upx;
		}

		.line {
			height: 25upx;
			width: 2upx;
			background: #fff;
			margin: 0 18upx;
		}

	}

	.tabnav {
		text-align: center;
		margin: 30upx 0;

		.line {
			width: 2upx;
			height: 60upx;
			background: #d9d9d9;
		}

		.tab-item {

			.title {
				color: #000;
				font-weight: blod;
				font-size: 28upx;
			}

			.tag {
				font-size: 22upx;
				color: #848484;
				width: 120upx;
				height: 35upx;
				line-height: 35upx;
				border-radius: 100upx;
				margin: 10upx auto 0;
			}

			&.active {
				.tag {
					background-image: linear-gradient(45deg, #fe8c2d, #fe5504);
					color: #fff;
				}

				.title {
					color: #f65900;
				}
			}
		}
	}

	.list {
		margin: 0 25upx;

		&>goods {
			margin-bottom: 30upx;
		}
	}
</style>
