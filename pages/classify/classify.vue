<template>
	<view class="pageview flex">
		<scroll-view class="menu" scroll-y scroll-with-animation>
			<view v-for="(item,index) in tabbar" :key="index" class="tab-bar-item" :class="[currentTab==index ? 'active' : '']"
			 :data-current="index" @tap.stop="swichNav">
				<text>{{item}}</text>
			</view>
		</scroll-view>
		<scroll-view class="flex-sub tab-view" scroll-y scroll-with-animation :scroll-top="scrollTop" @scroll="scroll">
			<tui-divider width="60%" :gradual="true">品种</tui-divider>
			<view class="menulist flex flex-wrap">
				<view class="menu-item" v-for="(item,index) in 20" :key="index">
					<image src="../../static/demo/1.png" mode="widthFix"></image>
					<p>卡罗拉</p>
				</view>
			</view>
		</scroll-view>

	</view>
</template>

<script>
	import tuiDivider from "@/components/divider/divider"
	export default {
		data() {
			return {
				tabbar: ["推荐分类", "进口超市", "国际名牌", "奢侈品", "海囤全球", "男装", "女装", "男鞋", "女鞋", "钟表珠宝", "手机数码", "电脑办公", "家用电器", "玩具乐器",
					"运动户外", "宠物生活", "特产馆"
				],
				currentTab: 0,
				scrollTop: 0,
				old: {
					scrollTop: 0
				}
			};
		},
		components: {
			tuiDivider
		},
		methods: {
			swichNav(e) {
				let cur = e.currentTarget.dataset.current;
				if (this.currentTab == cur) {
					return false;
				} else {
					this.currentTab = cur;
					this.scrollTop = this.old.scrollTop
					this.$nextTick(function() {
						this.scrollTop = 0
					});
				}

			},
			scroll: function(e) {
				console.log(e)
				this.old.scrollTop = e.detail.scrollTop
			},
		}
	}
</script>

<style lang="scss">
	page,
	.pageview {
		height: 100%;
		width: 100%;
		overflow: hidden;

		.menu {
			height: 100%;
			width: 170upx;
			text-align: center;

			.tab-bar-item {
				line-height: 70upx;
				color: #000;
				font-size: 26upx;
				border-top: 3upx solid #fff;
				background: #f5f4f9;

				&.active {
					color: #fc743c;
					background: #fff;
				}
			}
		}

		.tab-view {
			height: 100%;

			.menulist {
				padding: 20upx;

				.menu-item {
					text-align: center;
					color: #000;
					font-size: 24upx;

					width: 30%;

					p {
						margin: 25upx 0;
					}

					image {
						display: block;
						width: 100%;
					}

					&:nth-child(3n+2) {
						margin: 0 5%;
					}
				}
			}
		}
	}
</style>
