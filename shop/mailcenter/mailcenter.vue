<template>
	<view class="pageview flex flex-direction">
		<image src="/static/shop/bg@2x.png" mode="widthFix" class="bg"></image>
		<cu-custom :bgColor="bgColor" :isBack="true">
			<block slot="content">商家中心</block>
		</cu-custom>

		<div class="mailInfo flex">
			<div class="imgbox">
				<image src="../../static/demo/1.png"></image>
			</div>
			<div class="info flex-sub">
				<div class="name">方德玫瑰</div>
				<p>类别：品牌供应商</p>
				<p>平台佣金比例：5%</p>
				<navigator class="edit" url="/shop/mailinfo/mailinfo">
					<text>编辑</text>
					<image src="../../static/shop/edit@2x.png" mode="widthFix"></image>
				</navigator>
				<div class="state">
					<text :class="{'green':SwitchA}">{{SwitchA?'营业中':'未营业'}}</text>
					<switch class="green" @change="SwitchA" :class="switchA?'checked':''" :checked="switchA?true:false"></switch>
				</div>
			</div>
		</div>
		<div class="flex-sub main">
			<div class="title-bar">
				商家概况
			</div>
			<div class="grid col-4 cu-list">
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>总收入(元)</view>
				</view>
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>购买人数(人)</view>
				</view>
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>订单总数(单)</view>
				</view>
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>总销量(扎)</view>
				</view>
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>已提现(元)</view>
				</view>
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>账户余额(元)</view>
				</view>
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>提现中(元)</view>
				</view>
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>结算中(元)</view>
				</view>
			</div>
			<div class="title-bar">
				今日详情
			</div>
			<div class="grid col-4 cu-list">
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>订单总数(笔)</view>
				</view>
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>花材种类</view>
				</view>
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>销售数量(扎)</view>
				</view>
				<view class="menu-item">
					<view class="num">476.88</view>
					<view>销售额(元)</view>
				</view>

			</div>
			<div class="title-bar flex justify-between align-center">
				<span>我的订单</span>
				<span class='more'>查看全部
					<text class="cuIcon-right"></text></span>
			</div>
			<div class="grid col-4 cu-list">
				<view class="menu-item">
					<view class="imgbox">
						<image src="../../static/shop/delivery@2x.png" mode="widthFix"></image>
					</view>
					<view>待配送</view>
				</view>
				<view class="menu-item">
					<view class="imgbox">
						<image src="../../static/shop/delivery_two@2x.png" mode="widthFix"></image>
					</view>
					<view>已配送</view>
				</view>
				<view class="menu-item">
					<view class="imgbox">
						<image src="../../static/shop/settlement@2x.png" mode="widthFix"></image>
						<view class="cu-tag badge">99+</view>
					</view>
					<view>结算中</view>
				</view>
				<view class="menu-item">
					<view class="imgbox">
						<image src="../../static/shop/completed@2x.png" mode="widthFix"></image>
					</view>
					<view>已完成</view>
				</view>

			</div>
			<view class="cu-list menu sm-border">
				<view class="cu-item arrow" v-for="(item,index) in menulist" :key="index">
					<view class="content">
						<navigator :url="item.url" :hover-class="none">{{item.name}}</navigator>
					</view>
				</view>
			</view>
		</div>
		<view class="cu-bar tabbar bg-white">
			<navigator class="action" url="/shop/goodslist/goodslist">
				<view class="cuIcon-cu-image">
					<image src="/static/shop/tabbar/management_default@2x.png"></image>
				</view>
				<view class="text-gray">产品管理</view>
			</navigator>
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
					<image src="/static/shop/tabbar/business_selected@2x.png"></image>
				</view>
				<view class="text-black">商家中心</view>
			</view>

		</view>
	</view>
</template>

<script>
	import cuCustom from '../../colorui/components/cu-custom.vue'
	export default {
		data() {
			return {
				bgColor: 'nobg',
				switchA: false,
				menulist: [{
						url: '',
						name: '我的钱包'
					},
					{
						url: '',
						name: '结算记录'
					},
					{
						url: '',
						name: '交易查询'
					},
					{
						url: '',
						name: '售后订单'
					},
					{
						url: '',
						name: '我的评价'
					}
				]
			};
		},
		components: {
			cuCustom
		},
		methods: {
			SwitchA(e) {
				this.switchA = e.detail.value
			},
		}
	}
</script>

<style lang="scss">
	.pageview {
		height: 100%;
		overflow: auto;
		position: relative;
	}

	.pageview .main {
		overflow: auto;
		-webkit-overflow-scrolling: touch
	}

	.bg {
		width: 100%;
		position: absolute;
		top: 0;
		left: 0;
		z-index: 0;
	}

	.mailInfo {
		color: #717171;
		font-size: 26upx;
		padding: 24upx;
		margin: 35upx 30upx 0;
		background: #fff;
		box-shadow: 0px 2upx 6upx 0px rgba(26, 170, 104, 0.27);
		border-radius: 12upx;
		z-index: 1;
		position: relative;

		.imgbox {
			width: 140upx;
			height: 140upx;
			border-radius: 100%;
			overflow: hidden;
			border: 1px solid #19A967;
			margin-right: 25upx;

			image {
				width: 102%;
				height: 102%;
			}
		}

		.name {
			color: #323232;
			font-size: 34upx;
			margin-bottom: 23upx;
		}

		p+p {
			margin-top: 15upx;
		}

		.edit {
			position: absolute;
			color: #BCBCBC;
			top: 35upx;
			right: 20upx;

			image {
				width: 34upx;
				vertical-align: middle;
			}

			text {
				vertical-align: middle;
				margin-right: 5upx;
			}
		}

		.state {
			position: absolute;
			right: 24upx;
			bottom: 20upx;

			text {
				margin-right: 17upx;
			}

			.green {
				color: #19A967;
			}
		}
	}

	.title-bar {
		color: #19A967;
		font-size: 32upx;
		position: relative;
		padding: 30upx;

		&:before {
			background: #19A967;
			width: 10upx;
			height: 40upx;
			border-radius: 5upx;
			display: block;
			content: '';
			position: absolute;
			left: 0;
			top: 50%;
			transform: translateY(-50%);
		}

		&:after {
			content: '';
			display: block;
			height: 1px;
			position: absolute;
			left: 30upx;
			bottom: 0;
			background: #eee;
			transform: scaleY(.5);
			right: 0;
		}

		.more {
			color: #545454;
			font-size: 26upx;
		}
	}

	.cu-list.grid {
		.menu-item {
			color: #A2A2A2;
			font-size: 24upx;
			padding: 30upx 0;
			position: relative;

			.num {
				color: #2E302F;
				font-size: 44upx;
				margin-bottom: 10upx;
			}

			.imgbox {
				position: relative;
				width: 48upx;
				margin:0 auto 10upx;
			}

			image {
				width: 48upx;
			}
		}
	}
</style>
