<template>
	<view class="card bg-white">
		<view class="card-hd flex align-center ">
			<view class="title">货位号：001</view>
			<view class="time flex-sub margin-left">2020-03-01 11:00:50</view>
			<view class="arrow">
				<text>详细</text>
				<text class="cuIcon-right"></text>
			</view>
		</view>
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
						<span class="flex-sub">A级；20支/扎；中熟A级；20</span>
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
			</view>
		</view>
		<view class="card-ft flex align-center justify-between">
			<view>
				总计：2种，10扎，
				<text class="price">50元</text>
			</view>
			<view class="btn">确认配送</view>
			<view class="btn cancelBtn">取消配送</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	}
};
</script>

<style lang="scss">
.card {
	box-shadow: 0px 4upx 16upx 0px rgba(213, 213, 213, 1);
	border-radius: 8upx;
	margin: 0 30upx 20upx;
	color: #2e2e2e;
	font-size: 28upx;
	padding: 0 15upx;
	.tablebox{
		padding: 30upx 0 0;
	}
	.card-hd {
		height: 84upx;
		padding: 0 10upx;
		color: #ababab;
		font-size: 26upx;
		border-bottom: 1px solid #ededed;
		.title{
			color: #FD3C3E;
			font-size: 30upx
		}
		.arrow{
			color: #19A967;
			font-size: 28upx;
		}
	}
	.card-ft {
		height: 100upx;
		.price{
			color: #FD3C3E
		}
		.btn {
			color: #fff;
			background: #19a967;
			border-radius: 8upx;
			width: 160upx;
			line-height: 56upx;
			text-align: center;
			&.cancelBtn{
				background:#FD3C3E ;
			}
		}
	}
}
</style>
