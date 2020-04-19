<template>
	<mescroll-uni :down="downOption" @down="downCallback" :up="upOption" @up="upCallback" @init="mescrollInit" :fixed="false">

		<view class="cashoutlist">
			<div class="cashout-item solid-bottom" v-for="(item, index) in list" :key="index">
				<div class="flex justify-between align-center">
					<div>
						<div class="num">+{{ item.num }}</div>
						<div class="time">2020-03-01 05:05:30</div>
					</div>
					<div class="state" :class="'state'+item.state">{{item.state|statefilter}}</div>
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
			upCallback(mescroll) {
				},
		},
		filters: {
			statefilter(value) {
				if(value==1){
					return '提现中'
				}else if(value==2){
					return '提现成功'
				}else{
					return '提现失败'
				}
			}
		}
	};
</script>

<style scoped>
	page {
		background: #fff;
	}

	
	.cashoutlist .cashout-item {
		padding: 40upx 30upx;
		color: #919191;
		font-size: 26upx;
	}

	
	.cashoutlist .cashout-item .num {
		color: #0E0B0E;
		font-size:38upx;
		margin-bottom: 26upx;
	}



	.cashoutlist .cashout-item .state {
		font-size: 32upx;
	}

	.cashoutlist .cashout-item .state.state1 {
		color: #FF9518;
	}

	.cashoutlist .cashout-item .state.state2 {
		color: #19A967;
	}

	.cashoutlist .cashout-item .state.state3 {
		color: #FD3C3E;
	}
</style>
