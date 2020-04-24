<template>
	<view class="view-page flex flex-direction">
		<!-- banner -->
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
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imglist: [{
					img: '/static/demo/banner2.jpg'
				}]
			};
		},
		components: {

		},
		methods: {

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
</style>
