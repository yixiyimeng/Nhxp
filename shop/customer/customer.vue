<template>
	<mescroll-uni :down="downOption" @down="downCallback" :up="upOption" @up="upCallback" @init="mescrollInit" :fixed="false">
		<view class="customerlist">
			<div class="customer-item" v-for="(item, index) in list" :key="index">
				<div class="titlebar flex justify-between align-center">
					<div class="flex-sub">寄过来的数量不对，寄过来的数量不对寄过来的数量不对而且没有...
					</div>
					<div class="state" :class="'state'+item.state">{{item.state|statefilter}}</div>
				</div>
				<div class="grid col-2 solid-top solid-bottom">
					<view>
						<span>商品：</span>
						<span>戴安娜玫瑰</span>
					</view>
					<view>
						<span>投诉金额：</span>
						<span>9.80</span>
					</view>
					<view>
						<span>下单日期：</span>
						<span>2019-03-01</span>
					</view>
					<view>
						<span>申诉日期：</span>
						<span>2019-03-05</span>
					</view>
				</div>
				<div class="footerbar flex justify-between align-center">
					<div class="flex-sub">
						理赔金额：<span class="price"><em>￥</em>19.8</span>
					</div>
					<div class="btn">查看</div>
				</div>
			</div>
		</view>
	</mescroll-uni>
</template>

<script>
	import MescrollUni from '@/components/mescroll-uni/mescroll-uni.vue';
	export default {
		data() {
			return {
				downOption: {
					use: true,
					auto: true //是否在初始化后,自动执行下拉回调callback; 默认true
				},
				upOption: {
					noMoreSize: 1,
					page: {
						num: 0,
						size: 10
					}
				},
				mescroll: null,
				list: [{
						num: 2000,
						state: 1,
						time: '2019-04-05  15:18:20'
					},
					{
						num: 2000,
						state: 2,
						time: '2019-04-05  15:18:20'
					},
					{
						num: 2000,
						state: 3,
						time: '2019-04-05  15:18:20'
					}
				]
			};
		},
		components: {
			MescrollUni
		},
		methods: {

			mescrollInit(mescroll) {
				this.mescroll = mescroll;
				// this.getGoodslist();
			},
			downCallback(mescroll) {
				mescroll.resetUpScroll();
			},
			/*上拉加载的回调*/
			upCallback(mescroll) {},
		},
		filters: {
			statefilter(value) {
				if (value == 1) {
					return '待处理'
				} else if (value == 2) {
					return '已处理'
				}
			}
		}
	};
</script>

<style scoped>
	page {
		background: #fff;
	}

	.customerlist {
		padding: 0 30upx;
	}

	.customer-item {
		margin-top: 20upx;
		box-shadow: 0px 4upx 16upx 0px rgba(213, 213, 213, 1);
		border-radius: 8upx;
		padding: 8upx 25upx 0 25upx;
		font-size: 26upx;
		color: #8D8D8D;
	}

	.customer-item .titlebar {
		padding: 24upx 0;
		font-size: 30upx;

	}

	.customer-item .titlebar .flex-sub {
		color: #FD3C3E;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
		width: 100upx;
		margin-right: 20upx;
	}
	.customer-item .titlebar .state.state1{
		color: #FF9518;
	}
	.customer-item .titlebar .state.state2{
		color: #19A967;
	}
	.customer-item .grid,.customer-item .grid>view{
		padding: 10upx 0;
	}
	.customer-item .grid>view>span+span{
		color: #454545;
	}
	.customer-item .footerbar{
		padding: 15upx 0;
	}
	.customer-item .footerbar .price{
		color: #FD3C3E;
		font-size: 36upx;
	}
	.customer-item .footerbar .price em{
		font-style: normal;
		font-size: 24upx;
	}
	.customer-item .footerbar  .btn{
		background: #19A967;
		border-radius: 8upx;
		width:140upx;
		height:58upx;
		line-height: 58upx;
		text-align: center;
		color: #fff;
	}
</style>
