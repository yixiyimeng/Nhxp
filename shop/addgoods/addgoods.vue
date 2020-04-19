<template>
	<view>
		<form>
			<view class="cu-form-group">
				<view class="title">商品分类：</view>
				<span>玫瑰类-红玫瑰</span>
			</view>
			<view class="cu-form-group">
				<view class="title">商品名称：</view>
				<input placeholder-style="color:#C4C4C4" placeholder="请输入商品标题" name="input"></input>
			</view>
			<view class="cu-form-group">
				<view class="title">商品等级：</view>
				<picker range-key="name" @change="PickerChange" :value="index" :range="picker">
					<view class="picker">
						<span :style="{color:index>-1?'':'#C4C4C4'}">{{index>-1?picker[index].name:'请选择'}}</span>
					</view>
				</picker>
			</view>
			<view class="cu-form-group">
				<view class="title">单位：</view>
				<picker range-key="name" @change="PickerChange" :value="index" :range="picker">
					<view class="picker">
						<span :style="{color:index>-1?'':'#C4C4C4'}">{{index>-1?picker[index].name:'请选择'}}</span>
					</view>
				</picker>
			</view>
			<view class="cu-form-group">
				<view class="title">长度：</view>
				<picker range-key="name" @change="PickerChange" :value="index" :range="picker">
					<view class="picker">
						<span :style="{color:index>-1?'':'#C4C4C4'}">{{index>-1?picker[index].name:'请选择'}}</span>
					</view>
				</picker>
			</view>
			<view class="cu-form-group">
				<view class="title">颜色：</view>
				<picker range-key="name" @change="PickerChange" :value="index" :range="picker">
					<view class="picker">
						<span :style="{color:index>-1?'':'#C4C4C4'}">{{index>-1?picker[index].name:'请选择'}}</span>
					</view>
				</picker>
			</view>
			<view class="cu-form-group">
				<view class="title">产地：</view>
				<input placeholder-style="color:#C4C4C4" placeholder="请输入产品产地(限4字)例如：云南玉溪" name="input"></input>
			</view>
			<view class="cu-form-group">
				<view class="title">优点：</view>
				<picker range-key="name" @change="PickerChange" :value="index" :range="picker">
					<view class="picker">
						<span :style="{color:index>-1?'':'#C4C4C4'}">{{index>-1?picker[index].name:'请选择'}}</span>
					</view>
				</picker>
			</view>
			<view class="cu-form-group">
				<view class="title">缺点：</view>
				<picker range-key="name" @change="PickerChange" :value="index" :range="picker">
					<view class="picker">
						<span :style="{color:index>-1?'':'#C4C4C4'}">{{index>-1?picker[index].name:'请选择'}}</span>
					</view>
				</picker>
			</view>
			<view class="cu-form-group">
				<view class="title">成熟度：</view>
				<picker range-key="name" @change="PickerChange" :value="index" :range="picker">
					<view class="picker">
						<span :style="{color:index>-1?'':'#C4C4C4'}">{{index>-1?picker[index].name:'请选择'}}</span>
					</view>
				</picker>
			</view>
			<view class="cu-form-group">
				<view class="title">库存：</view>
				<input type="number" placeholder-style="color:#C4C4C4" placeholder="请输入商品库存数量" name="input"></input>
			</view>
			<view class="cu-form-group">
				<view class="title">商品单价：</view>
				<input type="digit" placeholder-style="color:#C4C4C4" placeholder="请输入商品售卖单价" name="input"></input>
			</view>
			<view class="cu-form-group">
				<view class="title">是否特价：</view>

				<radio-group class="block" @change="RadioChange">
					<view>
						<label>
							<radio class='green radio' :class="radio=='yes'?'checked':''" :checked="radio=='yes'?true:false" value="yes"></radio>
							是
						</label>
						<label>
							<radio class='green radio margin-left-sm' :class="radio=='no'?'checked':''" :checked="radio=='no'?true:false"
							 value="no"></radio>
							否
						</label>
					</view>
				</radio-group>
			</view>

			<view class="cu-bar bg-white   solid-top">
				<view class="action">
					上传图片：
				</view>
				<view class="action">
					{{imgList.length}}/4
				</view>
			</view>
			<view class="cu-form-group ">
				<view class="grid col-4 grid-square flex-sub">
					<view class="bg-img" v-for="(item,index) in imgList" :key="index" @tap="ViewImage" :data-url="imgList[index]">
						<image :src="imgList[index]" mode="aspectFill"></image>
						<view class="cu-tag bg-red" @tap.stop="DelImg" :data-index="index">
							<text class='cuIcon-close'></text>
						</view>
					</view>
					<view class="solids" @tap="ChooseImage" v-if="imgList.length<4">
						<text class='cuIcon-cameraadd'></text>
					</view>
				</view>
			</view>
			<view class="cu-bar bg-white solid-top">
				<view class="action">
					商品描述：
				</view>
			</view>
			<view class="cu-form-group solid bg-white margin-left margin-right">
				<textarea maxlength="-1" placeholder="可简单描述您的商品..."></textarea>
			</view>
			<div class="sendBtn">
				确认提交
			</div>

		</form>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				index: -1,
				picker: [{
						id: 1,
						name: 'A级'
					}, {
						id: 2,
						name: 'B级'
					}, {
						id: 3,
						name: 'C级'
					},
					{
						id: 4,
						name: 'D级'
					}
				],
				radio: 'no',
				imgList: ['/static/demo/1.png']
			};
		},
		methods: {
			upload() {
				uni.chooseImage({
					count: 1, //默认9
					sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
					sourceType: ['album', 'camera'], //从相册选择
					success: function(res) {
						console.log(JSON.stringify(res.tempFilePaths));
					}
				});
			},
			PickerChange(e) {
				this.index = e.detail.value
			},
			RadioChange(e) {
				this.radio = e.detail.value
			},
		}
	}
</script>

<style lang="scss">
	page {
		height: 100%;
		background: #fff;
	}

	.tip {
		padding: 20upx 30upx;
		color: #545454;
		font-size: 26upx;
		line-height: 38upx;
		background: #F7F7F7;

		.cuIcon {
			color: #19A967;
			font-size: 48upx;
			margin-right: 10upx;
		}
	}

	.cu-form-group input {
		text-align: right;
	}

	.cu-form-group radio {
		transform: scale(.7);
		vertical-align: 3px;
	}

	.uploadCard {
		background: #fff;
		padding: 38upx 30upx;
	}

	.uploadCard .upload {
		width: 324upx;
		height: 279upx;
	}

	.sendBtn {
		width: 690upx;
		height: 100upx;
		background: #19A967;
		box-shadow: 0 9upx 27upx 0 rgba(25, 169, 103, 0.58);
		border-radius: 12upx;
		color: #fff;
		text-align: center;
		font-size: 30upx;
		line-height: 100upx;
		margin: 30upx auto
	}

	.txt {
		padding: 10upx 0 40upx;
		font-size: 26upx;
		text-align: center;
		color: #6F6F6F;

		navigator {
			color: #19A967;
			display: inline;
		}
	}
</style>
