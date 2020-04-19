<template>
	<view class="view-page flex flex-direction">
		<searchbar></searchbar>
		<div class="flex-sub grid flex" style="overflow: hidden;">
			<div class="submenu">
				<scroll-view scroll-y="true" class="scroll-view" :scroll-into-view="'head-' + cateIndex">
					<div class="submenu-item flex flex-align-center" :class="{ active: cateIndex == myitemIndex }" v-for="(item, myitemIndex) in menulist"
					 :key="myitemIndex" @click="scrollTo(myitemIndex, item)" :id="'head-' + myitemIndex">
						<i :class="{ show: item.num > 0 && myitemIndex != 0 && isOpen == 1 }">{{ item.num > 100 ? '99+' : item.num }}</i>
						<span class="cate " v-bind:style="{ color: item.color }">{{ item.name }}</span>
					</div>
				</scroll-view>
			</div>
			<div class="main flex-sub flex flex-direction" style="overflow: hidden; height: 100%;">
				<div class="filterbar">
					<div class="filter-item">销量</div>
					<div class="filter-item filter-item-price">价格</div>
				</div>
				<div class="flex-sub" style="overflow: auto;">
					<mescroll-uni :down="downOption" @down="downCallback" :up="upOption" @up="upCallback" @init="mescrollInit" :fixed="false">
						<goodsitem class="goods-item" v-for="(item, index) in 10" :key="index" :goodsinfo="item" @showMail="showMail" @buygoods="buygoods"></goodsitem>
					</mescroll-uni>
				</div>
			</div>
		</div>
		<tui-actionsheet :show="showActionSheet" :item-list="itemList" @click="itemClick" @cancel="showActionSheet=false"></tui-actionsheet>
		<view class="cu-modal bottom-modal" :class="showDetails?'show':''" @tap="showDetails=false">
			<view class="cu-dialog" @tap.stop="">
				<!-- 关闭 -->
				<span class="close" @tap="showDetails=false"></span>
				<view>
					<div class="mail-item ">
						<div class="flex">
							<div class="imgbox">
								<image src="/static/demo/demo.png" mode="widthFix"></image>
							</div>
							<div class="info flex-sub">
								<div class="name">
									完美鲜花批发
								</div>
								<div><span>库存:489</span><span class="ml25">销量:54</span></div>
								<div class="flex justify-between align-center mt20">
									<span class="price">
										<em>￥19.8</em>/扎
									</span>
									<shophandle :isShowMinus="true"></shophandle>
								</div>
							</div>
						</div>
						<div class="flex align-center mt20">
							<div class="tag tag1"></div>
							<div class="state">关注的店</div>
							<div class="mailname" @click="tapMailName">完美鲜花批发></div>
						</div>
						<div class="goodstag grid col-3 mt20">
							<view>等级:B级</view>
							<view>枝长:80CM</view>
							<view>产地:云南昆明</view>
							<view>优点:花头漂亮</view>
							<view>瑕疵:刺多</view>
							<view>成熟度:中熟</view>
						</div>
					</div>
					<div class="title">商品描述：</div>
					<p>爱上你是我今生最大的幸福，想你是我最甜蜜的痛苦。</p>
					<div class="btn">加入采购单</div>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import searchbar from '@/components/searchbar.vue';
	import goodsitem from '@/components/goodsitem.vue';
	import MescrollUni from '@/components/mescroll-uni/mescroll-uni.vue';
	import tuiActionsheet from "@/components/actionsheet/actionsheet"
import shophandle from '@/components/shophandle.vue'
	export default {
		data() {
			return {
				cateIndex: 0,
				menulist: [{
					name: '玫瑰',
					num: 0
				}, {
					name: '玫瑰12',
					num: 0
				}],
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
				showActionSheet: false,
				itemList: [{
					text: "只买TA的产品",
					color: "#1a1a1a"
				}, {
					text: "查看TA的信息",
					color: "#1a1a1a"
				}, {
					text: "查看TA的口碑",
					color: "#1a1a1a"
				}],
				showDetails: false
			};
		},
		components: {
			searchbar,
			goodsitem,
			MescrollUni,
			tuiActionsheet,
			shophandle
		},
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur;
			},
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
			showMail() {
				this.showActionSheet = true
			},
			itemClick: function(e) {
				let index = e.index;
				this.showActionSheet = false;
				// this.tui.toast(`您点击的按钮索引为：${index}`)
			},
			buygoods(){
				this.showDetails=true;
			}
		}
	};
</script>

<style lang="scss">
	page,
	.view-page {
		height: 100%;
		overflow: hidden;
		position: relative;
	}

	.mt20 {
		margin-top: 20upx;
	}

	.grid .submenu {
		width: 170upx;
		margin-right: 2upx;
		text-align: center;
		color: #6D6D6D;
		height: 100%;
		overflow: hidden;
		position: relative;
		/* border-right: 1px solid #eee; */
		/* border-top: 1px solid #eee; */
		background: #FBFBFB;
	}

	.grid .submenu:after {
		content: '';
		position: absolute;
		right: 0;
		width: 2upx;
		top: 0;
		bottom: 0;
		background: #DBDBDB;
	}

	.grid .submenu .submenu-item {
		height: 100upx;
		border-bottom: 1px solid transparent;
		padding: 0 20upx;
		text-align: center;
		position: relative;
		z-index: 99;
	}

	.grid .submenu .submenu-item.active {
		color: #FF5454;
		background: #fff;
		border-bottom: 1px solid #DBDBDB;
	}

	.grid .submenu .submenu-item.active:before {
		content: '';
		position: absolute;
		left: 0;
		width: 6upx;
		height: 46upx;
		top: 50%;
		transform: translateY(-50%);
		background: #ff5454;
	}

	.grid .submenu .submenu-item.active:after {
		content: '';
		position: absolute;
		right: -10upx;
		width: 20upx;
		top: 0;
		bottom: 0;
		background: #fff;
	}

	.grid .submenu .submenu-item span {
		line-height: 100upx;
		display: block;
		width: 100%;
	}

	.grid .submenu .submenu-item i {
		display: none;
		font-style: normal;
		color: #fff;
		background: #ff5454;
		position: absolute;
		top: 0;
		right: 0;
		border-radius: 20upx;
		padding: 2upx 12upx;
		font-size: 20upx;
		line-height: 25upx;
	}

	.grid .submenu .submenu-item i.show {
		display: block;
	}

	.filterbar {
		line-height: 100upx;
		overflow: hidden;
		padding-right: 30upx;
	}

	.filterbar .filter-item {
		float: right;
		color: #ADADAD;
		font-size: 26upx;
		margin-left: 50upx;
	}

	.cu-dialog {
		padding: 50upx 30upx 70upx;
		background: #fff;
		position: relative;
		text-align: left;

		.close {
			position: absolute;
			right: 52upx;
			top: 35upx;
			height: 44upx;
			width: 44upx;
			background: url(../../static/window_close@2x.png) no-repeat center center;
			background-size: 100% auto;
			z-index: 99;
		}

		.title {
			color: #1D1D1D;
			font-size: 28upx;

			&+p {
				color: #808080;
				font-size: 25upx;
				margin: 24upx 0 58upx
			}
		}
		.btn{
			width:520upx;
			height:80upx;
			background:rgba(251,89,95,1);
			box-shadow:0 11upx 16upx 0 rgba(251,89,95,0.17);
			border-radius:8upx;
			margin: 0 auto;
			color: #fff;
			font-size: 28upx;
			line-height: 80upx;
			text-align: center;
		}
	}

	.mail-item {
		text-align: left;
		padding: 22upx 15upx;
		font-size: 24upx;
		color: #9F9F9F;
		position: relative;

		.imgbox {
			width: 140upx;
			background: #fff;
			border: 1px solid #E8E8E8;
			border-radius: 10upx;
			margin-right: 16upx;

			image {
				width: 100%;
			}
		}

		.name {
			font-size: 26upx;
			color: #FF9518;
			margin-bottom: 18upx;
		}

		.price {
			font-size: 22upx;
			color: #C1C1C1;

			em {
				font-style: normal;
				display: inline-block;
				color: #FD3C3E;
				font-size: 28upx;
			}
		}

		.btn {
			background: #FF9518;
			font-size: 24upx;
			color: #fff;
			border-radius: 8upx;
			width: 110upx;
			height: 48upx;
			display: block;
			text-align: center;
			line-height: 48upx;
		}

		.state {
			color: #FF9518;
			font-size: 22upx;
			margin-left: 10upx;

		}

		.tag {
			width: 66upx;
			height: 23upx;
			background: no-repeat center center;
			background-size: 100% auto;
		}

		.tag1 {
			background-image: url(/static/proprietary_label@2x.png);
		}

		.tag2 {
			background-image: url(/static/brand_label@2x.png);
		}

		.tag3 {
			background-image: url(/static/base_tag@2x.png);
		}

		.tag4 {
			width: 22upx;
			height: 21upx;
			background-image: url(/static/base_tag@2x.png);
		}

		.mailname {
			color: #7E7E7E;
			font-size: 22upx;
			margin-left: 10upx;
		}

		.goodstag {
			background: #F5F5F5;
			padding: 25upx 10upx;
			border-radius: 8upx;
			color: #515151;
			font-size: 20upx;

			view {
				padding: 5upx 0;
			}
		}
	}
</style>
