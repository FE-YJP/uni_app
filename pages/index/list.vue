<template>
	<view>
		<view class="header">
			<text @click="Init()">综合</text>
			<text @click="Sell()">销量</text>
			<text @click="Price()">价格</text>
		</view>
		<navigator class="back" url="../index/index">
			返回
		</navigator>
		<view class="wrap">
			<view class="left item">
				<view class="item1" v-for="(item,i) in list" :key="i">
					<image class="image" v-if="i%2 == 0" :src="item" mode="widthFix"></image>
				</view>
			</view>
			<view class="right item">
				<view class="item2" v-for="(item,i) in list" :key="i">
					<image class="image" v-if="i%2 == 1" :src="item" mode="widthFix"></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				demolist:[
					'https://fakeimg.pl/250x400/?text=World',
					'https://fakeimg.pl/350x400/?text=World',
					'https://fakeimg.pl/350x500/?text=World',
					'https://fakeimg.pl/250x400/?text=World',
					'https://fakeimg.pl/350x500/?text=World',
					'https://fakeimg.pl/250x400/?text=World',
				],
				list:[
					'https://fakeimg.pl/250x400/?text=World',
					'https://fakeimg.pl/350x400/?text=World',
					'https://fakeimg.pl/350x500/?text=World',
					'https://fakeimg.pl/250x400/?text=World',
					'https://fakeimg.pl/250x400/?text=World',
					'https://fakeimg.pl/350x400/?text=World',
				],
			}
		},
		methods: {
			Init(){
				this.list = this.demolist;
			},
			Sell(){
				this.list = this.demolist;
			},
			Price(){
				this.list = this.demolist;
			}
		},
		onReachBottom(){
			uni.showLoading({
			    title: '加载中'
			});
			if(this.list.length > 30){
				uni.showToast({
					icon:'none',
				    title: '暂无更多',
				    duration: 2000
				});
				return;
			}
			setTimeout(()=>{
				this.list = this.list.concat(this.demolist);
			    uni.hideLoading();
			}, 300);
		}
	}
</script>

<style>
.wrap{
	display: flex;
	width:100%;
	margin-top:100rpx;
}
.back{
	position: fixed;
	display: block;
	top:20rpx;
	left:20rpx;
	width: 80rpx;
	height: 60rpx;
	border-radius: 20rpx;
	background-color:#fff;
	color:#223322;
	box-shadow: 0 0 10px 0 rgba(0,0,0,.3);
	z-index: 100;
	font-size: 24rpx;
	text-align: center;
	line-height: 60rpx;
}
.header{
	text-align: center;
	height:100rpx;
	line-height: 100rpx;
	text-align: center;
	display: flex;
	justify-content: space-around;
	align-items:center;
	position:fixed;
	width:100%;
	z-index: 100;
	background: #007AFF;
	top:0;
	color:#fff;
}
.item{
	width:50%;
	display: flex;
	flex-direction: column;
	flex-shrink: 0;
	align-items: center;
}
.left,.right{
	
}
.item1{
	width:90%;
	border-radius: 20rpx;
	box-shadow: 0 0 10rpx 0 rgba(0,0,0,.2);
	margin:10rpx 0;
	text-align: center;
	box-sizing: border-box;
}
.item2{
	width:90%;
	border-radius: 20rpx;
	box-shadow: 0 0 10rpx 0 rgba(0,0,0,.2);
	margin:10rpx 0;
	text-align: center;
	box-sizing: border-box;
}
.image{
	width: 80%;
	heihgt:auto;
	margin: 20rpx auto;
	display: block;
}
</style>
