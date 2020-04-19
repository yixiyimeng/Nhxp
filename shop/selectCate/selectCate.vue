<template>
	<view class="pageview flex flex-direction">
		<scroll-view scroll-x class="bg-white nav topbar">
			<view class=" scrollview flex text-center">
				<span v-for="(item,index) in menulist" :key="index" :class="{'active':index==0}">{{item}}</span>
			</view>
		</scroll-view>

		<div class="main flex-sub">
			<mescroll-uni :down="downOption" @down="downCallback" :up="upOption" @up="upCallback" @init="mescrollInit" :fixed="false">
				<selectcate v-for="(item, index) in 10" :key="index" :goodsinfo="item"></selectcate>
			</mescroll-uni>
		</div>

	</view>
</template>

<script>
	import MescrollUni from '@/components/mescroll-uni/mescroll-uni.vue';
	import selectcate from '@/components/shop/selectcate.vue';
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
			selectcate
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
		-webkit-mask: -webkit-gradient(linear, left top, right bottom, from(rgba(0, 0, 0, 1)),color-stop(0.75,#fff),  to(rgba(0, 0, 0, 0)));
		
		.scrollview {
			line-height: 100upx;
			color: #A5A5A5;
			font-size: 30upx;

			span {
				position: relative;
				display: inline-block;

				&+span {
					margin-left: 65upx;
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
					bottom: 1upx;
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
