<template>
	<view>
		<view class="filterbar bg-white">
			<view class="filter-item flex align-center">
				<view class="title">起始日期：</view>
				<picker mode="date" class="flex-sub" :value="startDate" @change="TimeChange">
					<view class="inputbox  flex align-center">
						<text class="flex-sub">2020-12-12</text>
						<image src="../../static/shop/sessions@2x.png" mode="widthFix"></image>
					</view>
				</picker>

				<view class="line"></view>
				<picker mode="date" class="flex-sub" :value="startDate" @change="TimeChange">
					<view class="inputbox  flex align-center">
						<text class="flex-sub">第一场</text>
						<image src="../../static/shop/calendar@2x.png" mode="widthFix"></image>
					</view>
				</picker>
			</view>
			<view class="filter-item margin-top flex align-center">
				<view class="title">截至日期：</view>
				<picker mode="date" class="flex-sub" :value="startDate" @change="TimeChange">
					<view class="inputbox  flex align-center">
						<text class="flex-sub">2020-12-12</text>
						<image src="../../static/shop/sessions@2x.png" mode="widthFix"></image>
					</view>
				</picker>
				
				<view class="line"></view>
				<picker mode="date" class="flex-sub" :value="startDate" @change="TimeChange">
					<view class="inputbox  flex align-center">
						<text class="flex-sub">第一场</text>
						<image src="../../static/shop/calendar@2x.png" mode="widthFix"></image>
					</view>
				</picker>
			</view>
			<view class="searchBtn">查询</view>
		</view>
		<div class="space"></div>
		<view class="tablebox">
			<view class="table">
				<view class="table-hd flex">
					<span>品种</span>
					<span class="flex-sub">属性</span>
					<span>数量</span>
					<span>单价</span>
					<span>单价</span>
				</view>
				<view class="table-bd">
					<view class="table-td flex">
						<span>红玫瑰</span>
						<span class="flex-sub">A级；20支/扎；中熟</span>
						<span>5</span>
						<span>5</span>
						<span>25</span>
					</view>
					<view class="table-td flex">
						<span>红玫瑰</span>
						<span class="flex-sub">A级；20支/扎；中熟</span>
						<span>5</span>
						<span>5</span>
						<span>25</span>
					</view>
					<view class="table-td flex">
						<span>红玫瑰</span>
						<span class="flex-sub">A级；20支/扎；中熟</span>
						<span>5</span>
						<span>5</span>
						<span>25</span>
					</view>
				</view>
				<view class="table-ft flex">
					<span class="flex-sub text-right">合计:</span>
					<span>15</span>
					<span>14</span>
					<span>15</span>
				</view>
			</view>
			<view class="title margin-top-lg">备注：</view>
			<p>1、文案说明文案说明文案说明文案说明文案说明文案说明</p>
			<p>2、文案说明文案说明文案说明</p>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				startDate: ''
			};
		}
	}
</script>

<style lang="scss">
	.filterbar {
		padding: 35upx 30upx 50upx;

		.title {
			color: #2F2F2F;
			font-size: 30upx;
		}

		.inputbox {
			height: 70upx;
			line-height: 70upx;
			border: 1px solid #9D9D9D;
			border-radius: 8upx;
			padding: 0 18upx;

			image {
				width: 28upx;
			}
		}

		.line {
			width: 18upx;
			background: #E3E3E3;
			height: 3upx;
			margin: 0 10upx;
		}

		.searchBtn {
			width: 600upx;
			height: 100upx;
			background: rgba(25, 169, 103, 1);
			box-shadow: 0px 9upx 27upx 0px rgba(25, 169, 103, 0.58);
			border-radius: 12upx;
			color: #fff;
			color: #fff;
			font-size: 30upx;
			text-align: center;
			line-height: 100upx;
			margin: 46upx auto 0;
		}
	}

	.space {
		height: 14upx;
		background: #F5F5F5;
	}

	.tablebox{
		.title {
			color: #2E2E2E;
			font-size: 28upx;
			font-weight: bold;
		}
			
		p {
			margin-top: 30upx;
		}
	}
</style>
