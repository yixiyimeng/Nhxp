<template>
	<view class="pageview">
		<view class="group-row margin-top"><input placeholder="收货人姓名" name="input"></input></view>
		<view class="group-row"><input placeholder="收货人电话号码" name="input"></input></view>
		<view class="group-row">
			<picker mode="region" @change="RegionChange" :value="region">
				<view class="picker" :style="{'color':(region.length==3?'#000':'#878787')}">
					{{region.length==3?regionName:'选择省市区'}}
				</view>
			</picker>
		</view>
		<view class="group-row">
			<input placeholder="详细街道地址" name="input"></input>
		</view>
		<view class="flex justify-between group-row align-center">
			<view>
				<view class="title">设置为默认地址</view>
				<view>每次下单时会使用默认地址</view>
			</view>
			<switch class='orange' @change="changeDefault" :class="isDefault?'checked':''" :checked="isDefault?true:false"></switch>
		</view>
		<view class="submitBtn">保存</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				region: [],
				regionName: '',
				isDefault: true
			};
		},
		methods: {
			RegionChange(e) {
				this.region = e.detail.value;
				this.regionName = this.region.join(',')
			},
			changeDefault(e) {
				this.isDefault = e.detail.value;
			}
		}
	}
</script>

<style lang="scss">
	.pageview {
		margin: 0 40upx;
		font-size: 26upx;
		color: #878787;

		.group-row {
			padding: 30upx 20upx;
			border-bottom: 1px solid #e5e5e5;
			.title{
				color: #000;
				font-size: 28upx;
				margin-bottom: 15upx;
				font-weight: bold;
			}
			.picker{
				height: 1.4rem;
				line-height: 1.4rem;
			}
		}
		.submitBtn{
			margin-top: 45upx;
		}
	}
</style>
