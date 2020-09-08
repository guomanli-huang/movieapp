<template>
	<view class="movie">
		<view class="movieimg">
			<image class="imagesmsg" src="https://img3.doubanio.com/dae/staticng/search_static/ithil/gen/icon_movie_af099086f0.svg"></image>
		</view>
		<view class="movieimg">	
		<image src="https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2616835570.webp" class="imagesmsg"></image>
		</view>
		
		<view class="detailmsg">
		<view class="detail">
			<view class="left">
					<image class="msgimg" src="https://img9.doubanio.com/view/photo/l/public/p2581163395.webp"></image>
				</view>
				<view class="right">
					<view>1.肖申克的救赎<text class="rate" style="color:#F0AD4E">9.7分</text></view>
					<view>2.霸王别姬<text class="rate" style="color:#F0AD4E">9.6分</text></view>
					<view>3.阿甘正传<text class="rate" style="color:#F0AD4E">9.5分</text></view>
				</view>
			</view>
		<!-- </view> -->
		<view class="detail">
			<view class="left">
					<image class="msgimg" src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1598972255815&di=23a3f8325653be3714e4e7ed6929847d&imgtype=0&src=http%3A%2F%2Fpptdown.pptbz.com%2Fpptbeijing%2F%25E7%2594%25B5%25E5%25BD%25B1PPT%25E8%2583%258C%25E6%2599%25AF%25E5%259B%25BE%25E7%2589%2587.jpg"></image>
				</view>
				<view class="right">
					<view>1.肖申克的救赎<text class="rate" style="color:#F0AD4E">9.7分</text></view>
					<view>2.霸王别姬<text class="rate" style="color:#F0AD4E">9.6分</text></view>
					<view>3.阿甘正传<text class="rate" style="color:#F0AD4E">9.5分</text></view>
				<!-- </view> -->
			</view>
		</view>
		<view class="detail">
			<view class="left">
					<image class="msgimg" src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1598972255815&di=635dd8e2e67b290f3587288ffcc1d060&imgtype=0&src=http%3A%2F%2Fimg1.juimg.com%2F180702%2F330804-1PF2022H647.jpg"></image>
				</view>
				<view class="right">
					<view>1.肖申克的救赎<text class="rate" style="color:#F0AD4E">9.7分</text></view>
					<view>2.霸王别姬<text class="rate" style="color:#F0AD4E">9.6分</text></view>
					<view>3.阿甘正传<text class="rate" style="color:#F0AD4E">9.5分</text></view>
				</view>
			<!-- </view> -->
		</view>
		<view class="detail">
			<view class="left">
					<image class="msgimg" src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1598972325434&di=5e5b5f3e2380186acec8b0d92196a15b&imgtype=0&src=http%3A%2F%2Fimg2.imgtn.bdimg.com%2Fit%2Fu%3D3212355327%2C3027938428%26fm%3D214%26gp%3D0.jpg"></image>
				</view>
				<view class="right">
					<view>1.肖申克的救赎<text class="rate" style="color:#F0AD4E">9.7分</text></view>
					<view>2.霸王别姬<text class="rate" style="color:#F0AD4E">9.6分</text></view>
					<view>3.阿甘正传<text class="rate" style="color:#F0AD4E">9.5分</text></view>
				</view>
			<!-- </view> -->
		</view>
		<view class="detail">
			<view class="left">
					<image class="msgimg" src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1598972347945&di=13afe8a93b1eb5e8222d89a682a3fa38&imgtype=0&src=http%3A%2F%2F5b0988e595225.cdn.sohucs.com%2Fimages%2F20170613%2F7d0bab8058964c6a84fb4d7be0003ce8.png"></image>
				</view>
				<view class="right">
					<view>1.肖申克的救赎<text class="rate" style="color:#F0AD4E">9.7分</text></view>
					<view>2.霸王别姬<text class="rate" style="color:#F0AD4E">9.6分</text></view>
					<view>3.阿甘正传<text class="rate" style="color:#F0AD4E">9.5分</text></view>
				</view>
			</view>
		<!-- </view> -->
		</view>
	</view>
</template>

<script>
	// https://flvplayer.js.org
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="less" scoped>
.movie{
	display: flex;
	flex-direction: column;
	padding: 10px;
	box-sizing: border-box;
	align-items: center;
	.movieimg{
		margin-bottom: 20px;
		width: 720rpx;
		height: 150px;
		// border: 1px solid #4CD964;
		// background-color: #4CD964;
		.imagesmsg{
			width: 720rpx;
			height: 150px;
		}
	}
	.detailmsg{
		display: flex;
		width: 750rpx;
		flex-direction: column;
		// margin-bottom: 20px !important;
			.detail{
				width: 750rpx;
				padding: 10px;
				box-sizing: border-box;
				display: flex;
				justify-content: space-between;
				height: 100px;
				align-items: center;
				margin-bottom: 20px !important;
				.left{
					flex: 0 0 50px;
					.msgimg{
						width: 100px;
						height: 100px;
					}
					
				}
				.right{
					flex: 1;
					border: 1px solid #ddd;
					border-left: 0;
				    height: 90px;
					// display: flex;
					// flex-direction: column;
					// align-items: center;
					view{
						margin-left: 20px;
						margin-bottom: 5px;
						font-size: 12px;
						margin-top: 10px
						// text{
						// 	// color:#ffff66;
						// }
						// .rate{
						// 	 color:#ffff66;
						// }
					}
				}
			}
		
	}
}
</style>
