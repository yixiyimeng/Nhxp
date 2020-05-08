<template>
	<view class="view-page flex flex-direction">
		<view class="bg-white">
			<view class="bg-white" style="z-index: 999; position: relative;">
				<searchbar></searchbar>
				<view class="topbar flex align-center">
					<view class="flex-sub">
						<scroll-view scroll-x class=" nav  ">
							<view class=" scrollview flex text-center">
								<span v-for="(item,index) in menulist" :key="index" :class="{'active':index==0}">{{item}}</span>
							</view>
						</scroll-view>
					</view>
					<span class="line"></span>
					<span class="arrow" @tap="isShowAllmenu=!isShowAllmenu"></span>
				</view>
			</view>
			<view class="cu-modal top-modal" :class="isShowAllmenu?'show':''" @tap="isShowAllmenu=!isShowAllmenu">
				<view class="cu-dialog  bg-white" @tap.stop="">
					<view class="padding-sm">
						<view class='cu-tag round bg-orange'>圆角</view>
						<view class='cu-tag round'>圆角</view>
						<view class='cu-tag round'>圆角</view>
						<view class='cu-tag round'>圆角</view>
					</view>
				</view>
			</view>
			<view class="filterbar flex align-center">
				<span class="active">默认</span>
				<span>
					<text>销售</text>
					<image src="../../static/icon25.png" mode="widthFix"></image>
				</span>
				<span>
					<text>价格</text>
					<image src="../../static/icon25.png" mode="widthFix"></image>
				</span>
				<span class="filter">
					<text>筛选</text>
					<image src="../../static/icon24.png" mode="widthFix"></image>
				</span>
			</view>
		</view>

		<view class="flex-sub main">
			<mescroll-uni :down="downOption" @down="downCallback" :up="upOption" @up="upCallback" @init="mescrollInit" :fixed="false">
				<goodsitem class="goods-item" v-for="(item, index) in 10" :key="index" :goodsinfo="item" @showMail="showMail"
				 @buygoods="buygoods"></goodsitem>
			</mescroll-uni>
		</view>
		<!-- 查看店铺 -->
		<view class="cu-modal bottom-modal" :class="isShowShop?'show':''">
			<view class="cu-dialog bg-white">
				<view class="cu-bar ">
					<view class="action title">查看店铺</view>
					<view class="action cuIcon-close" @tap="hideModal"></view>
				</view>
				<view class="action-list">
					<view class="action-item">进入店铺</view>
					<view class="action-item">查看评价</view>
				</view>
			</view>
		</view>
		<!-- 查看评价 -->
		<view class="cu-modal" :class="isShowReply?'show':''">
			<view class="cu-dialog bg-white">
				<view class="cu-bar solids-bottom">
					<view class="action title">他的评价</view>
					<view class="action cuIcon-close" @tap="hideModal"></view>
				</view>
				<view class="padding-lg replylist">
					<!-- <cmt-reply v-for="(item,index) in 2" :key="index"></cmt-reply> -->
					<mescroll-empty :option="emptyoption"></mescroll-empty>
				</view>
				<view class="cu-modal-ft">点击商品详情查看更多评价 ></view>
			</view>
		</view>
		<!-- 商品详情 -->
		<view class="cu-modal bottom-modal" :class="showDetails?'show':''" @tap="showDetails=false">
			<view class="cu-dialog bg-white" @tap.stop="" style="padding-top: 20px;">
				<!-- 关闭 -->
				<view class="action cuIcon-close close" @tap="showDetails=false"></view>
				<view class="mail-item" style="max-height: 70vh;overflow: auto;">
					<div class="flex align-center">
						<div class="imgbox">
							<image src="/static/demo/1.png" mode="widthFix"></image>
						</div>
						<div class="info flex-sub">
							<div class="name">
								完美鲜花批发
							</div>
							<div class="price margin-bottom margin-top">
								￥19.8
							</div>
							<div><span>库存:489</span><span class="margin-left">销量:54</span></div>

						</div>
					</div>
					<div class="flex justify-between">
						<div class="flex align-center margin-top-sm">
							<div class="tag tag1">自营</div>
							<div class="state">关注的店</div>
							<div class="mailname" @click="tapMailName">完美鲜花批发></div>
						</div>
						<numberbox :value='num' @change="changeNum"></numberbox>
					</div>
					<div class="goodstag grid col-3 margin-top-sm">
						<view>等级:B级</view>
						<view>枝长:80CM</view>
						<view>产地:云南昆明</view>
						<view>优点:花头漂亮</view>
						<view>瑕疵:刺多</view>
						<view>成熟度:中熟</view>
					</div>
					<view class="goodsinfo">
						<div class="title">商品描述：</div>
						<p>爱上你是我今生最大的幸福，想你是我最甜蜜的痛苦。</p>
					</view>
					<div class="addcarbtn">加入采购单</div>
				</view>
			</view>
		</view>
		<!-- 客服 -->
		<view class="cu-modal bottom-modal" :class="isContact?'show':''">
			<view class="cu-dialog bg-white">
				<view class="cu-bar ">
					<view class="action title">客服</view>
					<view class="action cuIcon-close" @tap="isContact=!isContact"></view>
				</view>

				<view class="action-list">
					<view class="action-item weixin flex align-center">
						<span>客服微信</span>
						<span class="flex-sub">12233333</span>
						<span class="copy" @tap="copy('122333')">复制</span>
					</view>
					<view class="action-item weixin flex align-center">
						<span>客服微信</span>
						<span class="flex-sub">12233333</span>
						<span class="copy" @tap="copy('122333')">复制</span>
					</view>
					<button open-type="contact" class="action-item">
						<view>在线客服</view>
					</button>
				</view>
			</view>
		</view>
		<!-- 筛选 条件 -->
		<view class="cu-modal drawer-modal justify-end" :class="isShowFilter?'show':''" @tap="isShowFilter=!isShowFilter">
			<view class="cu-dialog basis-xl flex flex-direction bg-white " @tap.stop="">
				<view class="flex-sub padding-lg">
					<view>
						<view>颜色</view>
						<view class="margin-top-sm">
							<view class='cu-tag radius bg-orange'>圆角</view>
							<view class='cu-tag radius'>圆角</view>
							<view class='cu-tag radius'>圆角</view>
							<view class='cu-tag radius'>圆角</view>
						</view>
					</view>
				</view>
				<view class="filterftbar flex justify-center">
					<span>重置</span>
					<span>确定</span>
				</view>
			</view>
		</view>

	</view>

</template>

<script>
	import searchbar from '@/components/searchbar.vue';
	import goodsitem from '@/components/goodsitem.vue';
	import tuiActionsheet from "@/components/actionsheet/actionsheet"
	import Numberbox from '@/components/numberbox.vue'
	import MescrollMixin from "@/components/mescroll-uni/mescroll-mixins.js"
	import cmtReply from "@/components/cmt-reply"
	import MescrollEmpty from "@/components/mescroll-uni/components/mescroll-empty"
	export default {
		data() {
			return {
				CustomBar: this.CustomBar,
				cateIndex: 0,
				menulist: ['全部', '玫瑰', '百合', '康乃馨', '梅花', '牡丹', '百合', '康乃馨', '梅花', '牡丹'],
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
				showDetails: false, //
				isShowShop: false, //查看店铺
				isShowReply: false, //查看评价
				isContact: false, //查看客服
				isShowFilter: false, //查看筛选条件
				isShowAllmenu: true, //查看所有分类
				emptyoption: {
					icon: '/static/empty.png',
					tip: '暂无产品评价'
				}
			};
		},
		components: {
			searchbar,
			goodsitem,
			tuiActionsheet,
			Numberbox,
			cmtReply,
			MescrollEmpty
		},
		mixins: [MescrollMixin],
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur;
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
			buygoods() {
				this.showDetails = true;
			},
			copy(value) {
				uni.setClipboardData({
					data: value,
					success: function() {
						console.log('success');
					}
				});
			},


		}
	};
</script>

<style lang="scss">
	page,
	.view-page {
		height: 100%;
		overflow: hidden;
		position: relative;
		background: #ededed;
	}

	.topbar {
		height: 110upx;
		position: relative;


		&>.flex-sub {
			width: 200rpx;
			padding-left: 25upx;
			padding-right: 5upx;
		}

		.nav {
			height: 106upx;
		}

		.scrollview {
			line-height: 106upx;
			color: #000;
			font-weight: blod;
			font-size: 28upx;

			span {
				position: relative;
				display: inline-block;

				&+span {
					margin-left: 50upx;
				}

				&.active {
					color: #fc733b;
					font-size: 32upx;
				}


			}
		}

		.line {
			width: 2upx;
			height: 55upx;
			display: block;
			background: url(../../static/icon23.png) no-repeat center center;
			background-size: 2upx auto;
		}

		.arrow {
			width: 86upx;
			height: 100%;
			display: block;
			background: url(../../static/icon22.png) no-repeat center center;
			background-size: 36upx auto;
		}
	}

	.filterbar {
		height: 70upx;
		border-top: 2upx solid #ededed;

		&>span {
			width: 25%;
			color: #727272;
			text-align: center;
			font-size: 28upx;

			&.active {
				color: #fc743c;
			}

			image {
				width: 10upx;
				margin-left: 10upx;
			}

			&.filter {
				image {
					width: 18upx;
				}
			}
		}
	}

	.main {
		overflow: auto;
		margin-top: 30upx;
	}

	.action-list {
		.action-item {
			color: #ff6202;
			font-size: 28upx;
			line-height: 140upx;
			text-align: center;
			padding: 0 75upx;
			background: #fff;
			border-top: 1px solid #eee;

			&>span {
				color: #000;

				&.flex-sub {
					text-align: center;
				}

				&.copy {
					color: #ff6202;
					border: 1px solid #ff6202;
					height: 50upx;
					width: 100upx;
					line-height: 50upx;
					border-radius: 100upx;
					font-size: 24upx;
				}
			}
		}
	}

	.cu-modal {
		.cu-dialog {
			width: 600upx;
			text-align: left;
			position: relative;
		}

		.title {
			color: #000;
			font-size: 28upx;
			font-weight: blod;
		}

		.cuIcon-close {
			font-size: 40upx;
			color: #303030;
		}

		.cu-modal-ft {
			color: #fff;
			text-align: center;
			font-size: 24upx;
			line-height: 70upx;
			background: #ff6202;
		}

		.replylist {
			max-height: 300px;
			overflow: auto;
		}

		.close {
			position: absolute;
			right: 56upx;
			top: 30upx;
		}
	}

	.mail-item {
		text-align: left;
		font-size: 24upx;
		color: #9F9F9F;
		padding: 40upx 50upx;
		position: relative;


		.imgbox {
			width: 200upx;
			background: #fff;
			border: 1px solid #E8E8E8;
			border-radius: 10upx;
			margin-right: 50upx;

			image {
				width: 100%;
			}
		}

		.name {
			font-size: 34upx;
			color: #000;
			font-weight: bold;
		}

		.price {
			font-style: normal;
			display: inline-block;
			color: #e03d3e;
			font-size: 38upx;
		}

		.addcarbtn {
			font-size: 30upx;
			color: #fff;
			border-radius: 16upx;
			width: 100%;
			height: 100upx;
			display: block;
			text-align: center;
			line-height: 100upx;
			margin-top: 20upx;
			background-image: linear-gradient(#fb9449, #fc753c);
		}

		.state {
			color: #FF9518;
			font-size: 22upx;
			margin-left: 10upx;

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

		.mailname {
			color: #7E7E7E;
			font-size: 22upx;
			margin-left: 10upx;
		}

		.goodstag {
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

		.goodsinfo {
			font-size: 20upx;

			.title {
				color: #000;
				font-size: 28upx;
			}

			p {
				margin: 20upx 0;
			}

		}
	}

	/* 筛选 */
	.drawer-modal {
		.title {
			font-size: 30upx;
			color: #000;
		}

		.cu-tag {
			padding: 0 48upx;
			height: 60upx;
			margin: 20upx 10upx;
		}

		.filterftbar {
			padding: 50upx 0;

			span {
				width: 150upx;
				height: 60upx;
				line-height: 60upx;
				color: #fc743b;
				border: 1px solid #fc743b;
				border-radius: 10upx;
				text-align: center;

				&+span {
					margin-left: 120upx;
					color: #fff;
					background-image: linear-gradient(90deg, #fe8c2d, #fe5504);
				}
			}
		}
	}

	/* 所有分类 */
	.top-modal {
		top: 180upx;
		z-index: 998;

		.cu-tag {
			line-height: 62upx;
			padding: 0 25upx;
			margin: 10upx 15upx;
			font-size: 28upx;
		}
	}
</style>
