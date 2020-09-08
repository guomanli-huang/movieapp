<template>
	<view class="my">
		<view class="login">
			<view class="loginbtn">登录</view>
		</view>
		<view class="title">
			<text class="left">我的书影音</text>
			<text class="right">登录查看&gt</text>
		</view>
		<view class="bookmsg" v-for="(item,index) in list" :key="index">
			
			<view class="analyse">
				<view class="imgs">
					<image :src="item.url" style="width: 25px;height: 25px;"></image>
					<view class="look">
						<view class="top">{{item.title}}</view>
						<view class="bottom"><text>{{item.num}}</text>{{item.decsimg}}</view>
					</view>
				</view>
                <view class="watchrecode">
					<view class="watch">
						<view>{{item.descone}}</view>
						<view>{{item.desctwo}}</view>
						</view>
					<view class="immediately">
						<view class="immediatelybtn">
							立即开启
						</view>
						<text>&gt</text>
					</view>
				</view>
   
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
           list:[
			   {url:"../../static/icon_4.png",title:"观影分析",num:0,decsimg:"看过",descone:"标记十部影片",desctwo:"开启观影分析"},			   {url:"../../static/icon_5.png",title:"读书分析",num:0,decsimg:"读过",descone:"标记十部书",desctwo:"开启读书分析"},
			   			   {url:"../../static/icon_6.png",title:"音乐分析",num:0,decsimg:"听过",descone:"标记十部唱片",desctwo:"开启音乐分析"}
		   ]
			}
		},
		methods: {

		}
	}
</script>

<style lang="less" scoped>
	.my {
		display: flex;
		flex-direction: column;

		.login {
			width: 750rpx;
			height: 180px;
			background-color: #ffff66;

			// line-height: 90px;
			.loginbtn {
				margin: 50px auto;
				width: 400rpx;
				height: 45px;
				text-align: center;
				line-height: 45px;
				background-color: #fff;
				border-radius: 15px;
			}
		}
         .title {
				display: flex;
				justify-content: space-between;
				padding: 10px;
				box-sizing: border-box;
				.left {
						font-weight: bold;
						font-size: 18px;
					}
				
					.right {
						color: #ccc;
						font-size: 12px;
					}
				}
		.bookmsg {
			

				
			.analyse{
				display: flex;
				justify-content: space-between;
				height: 100px;
				width: 750rpx;
				padding: 10px;
				box-sizing: border-box;
				.imgs{
					display:flex;
					width:200rpx;
					height:100%;
					justify-content: space-between;
					.look{
						font-size: 14px;
					}
				}
				.watchrecode{
					display: flex;
					justify-content: space-between;
					.watch{
						flex: 1;
						display: flex;
						flex-direction: column;
						color: #ddd;
						font-size: 14px;
						margin-right: 10px;
					}
					.immediately{
						width: 120px;
						display: flex;
						justify-content: space-around;
						.immediatelybtn{
							width: 80px;
							height: 30px;
							background-color: #ddd;
							line-height: 30px;
							font-size: 14px;
							text-align: center;
						}
					}
				}
			}

		}
	}
</style>
