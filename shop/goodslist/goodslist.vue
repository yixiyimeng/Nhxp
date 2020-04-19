<template>
	<view class="pageview flex flex-direction">
		<div class="topbar flex align-center">
			<!-- <div class="flex-sub scrollview">
				<span v-for="(item,index) in menulist" :key="index" :class="{'active':index==0}">{{item}}</span>
			</div> -->
			<div class="flex-sub">
				<scroll-view scroll-x class="bg-white nav scrollview ">
					<view class="  flex text-center">
						<span v-for="(item,index) in menulist" :key="index" :class="{'active':index==0}">{{item}}</span>
					</view>
				</scroll-view>
			</div>
			<navigator class="add" url="/shop/selectCate/selectCate">
				<text class="cuIcon-add"></text>
				<text>添加产品</text>
			</navigator>
		</div>
		<div class="main flex-sub">
			<mescroll-uni :down="downOption" @down="downCallback" :up="upOption" @up="upCallback" @init="mescrollInit" :fixed="false">
				<cate v-for="(item, index) in 10" :key="index" :goodsinfo="item"></cate>
			</mescroll-uni>
		</div>
		<view class="cu-bar tabbar bg-white">
			<view class="action">
				<view class="cuIcon-cu-image">
					<image src="/static/shop/tabbar/management_selected@2x.png"></image>
				</view>
				<view class="text-black">产品管理</view>
			</view>
			<view class="action">
				<view class="cuIcon-cu-image">
					<image src="/static/shop/tabbar/order_default@2x.png"></image>
				</view>
				<view class="text-gray">订单</view>
			</view>
			<view class="action">
				<view class="cuIcon-cu-image">
					<image src="/static/shop/tabbar/summary_default@2x.png"></image>
				</view>
				<view class="text-gray">订单汇总</view>
			</view>

			<view class="action">
				<view class="cuIcon-cu-image">
					<image src="/static/shop/tabbar/business_default@2x.png"></image>
				</view>
				<view class="text-gray">商家中心</view>
			</view>

		</view>
	</view>
</template>

<script>
	import MescrollUni from '@/components/mescroll-uni/mescroll-uni.vue';
	import cate from '@/components/shop/cate.vue';
	export default {
		data() {
			return {
				menulist: ['全部', '玫瑰', '百合', '康乃馨', '梅花', '牡丹'],
				downOption: {
					use: true,
					auto: false //是否在初始化后,自动执行下拉回调callback; 默认true
				},
				upOption: {
					noMoreSize: 1,
					page: {
						num: 0,
						size: 10
					},
				},
				mescroll: null, //mescroll实例对象

			};
		},
		components: {
			MescrollUni,
			cate
		},
		methods: {
			mescrollInit(mescroll) {
				this.mescroll = mescroll;
			},
			/*下拉刷新的回调, 有三种处理方式: */
			downCallback(mescroll) {
				mescroll.resetUpScroll(); // 重置列表为第一页 (自动执行 page.num=1, 再触发upCallback方法 )
			},
			/*上拉加载的回调*/
			upCallback(mescroll) {

			},

		}
	}
</script>

<style lang="scss">
	.pageview {
		height: 100%;
	}

	.pageview .main {
		overflow: auto;
	}

	.pageview .main .cate-item {
		margin: 20upx 30upx;
	}

	.topbar {
		height: 100upx;
		padding: 0 30upx;
		border-bottom: 1px solid #EAEAEA;

		&>.flex-sub {
			width: 200upx;
		}

		.add {
			width: 190upx;
			height: 64upx;
			background: rgba(25, 169, 103, 1);
			box-shadow: 0 2upx 9upx 0 rgba(25, 169, 103, 0.58);
			border-radius: 8upx;
			font-size: 26upx;
			color: #fff;
			line-height: 64upx;
			text-align: center;
			margin-left: 25upx;

			.cuIcon-add {
				font-size: 30upx;
			}
		}

		.scrollview {
			line-height: 100upx;
			color: #A5A5A5;
			font-size: 30upx;
			width: 100%;
			-webkit-mask: -webkit-gradient(linear, left top, right bottom, from(rgba(0, 0, 0, 1)),color-stop(0.75,#fff),  to(rgba(0, 0, 0, 0)));

			span {
				position: relative;
				display: inline-block;

				&+span {
					margin-left: 35upx;
				}

				&.active {
					color: #19A967;
				}

				&.active:after {
					content: '';
					background: #19A967;
					display: block;
					height: 5upx;
					width: 35upx;
					position: absolute;
					bottom: 0;
					left: 50%;
					transform: translateX(-50%);
				}
			}
		}
	}

	.tabbar {
		border-top: 1px solid #F1F1F1;
	}
</style>
