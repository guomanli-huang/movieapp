<template>
	<view class="detail">
		<scroll-view scroll-y="true">
		<view class="detailmsg">
			<view class="left">
				<image :src="datalist.images.large" class="leftmsg"></image>
			</view>
			<view class="right">
				<view class="righttitle">{{datalist.title}}({{datalist.year}})</view>
				<view class="moviecate">剧情
					<text v-for="item in datalist.genres">{{item}}/</text>
					<text>{{datalist.countries}}/</text>
					<text>片长{{datalist.reviews_count}}分钟</text>
				</view>
				<view class="clickbtn">
					<view class="clickbtnone">
						<image src="/static/icon_6.png" class="msgset"></image>想看
					</view>
					<view class="clickbtntwo">
						<image src="/static/icon_7.png" class="msgset"></image>看过
					</view>
				</view>
			</view>
		</view>
		<view class="ratemsg">
			<view class="ratetitle">
				<text>豆瓣评分</text>
				<text>></text>
			</view>
			<view class="startrate">
				<view class="left">
					<view>{{datalist.rating.average}}</view>
					<uni-rate :max="5" :value="datalist.rating.average/2" :size="10" class="start" />
				</view>
				<view class="right">
					<view class="leftdis">
						<uni-rate :max="5" :value="0" :size="10" />
						<uni-rate :max="4" :value="0" :size="10" />
						<uni-rate :max="3" :value="0" :size="10" />
						<uni-rate :max="2" :value="0" :size="10" />
						<uni-rate :max="1" :value="0" :size="10" />
					</view>
					<view class="rightdis">
						<view class="box"></view>
						<view class="box"></view>
						<view class="box"></view>
						<view class="box"></view>
						<view class="box"></view>
						<view class="boxrate">{{datalist.comments_count}}人评分</view>
					</view>
				</view>
			</view>

		</view>
		<view class="moviemsg">
			<view class="titleproduce">简介</view>
			<view>{{datalist.summary}}</view>
		</view>
		<view class="moviepeopel">
			<view class="title">影人</view>
			<scroll-view scroll-x class="scrollmsg">
			<view class="actor">
				<view class="actormsg" v-for="(item,index) in datalist.casts" :key="index">
					<image :src="item.avatars.large" class="imgs"></image>
					<text class="imgsname">{{item.name}}</text>
				</view>
			</view>
			</scroll-view>
		</view>
		</scroll-view>
	  </view>
	
</template>

<script>
	import {
		uniRate
	} from '@dcloudio/uni-ui'
	export default {
		data() {
			return {
				title: "",
				datalist: {}
			}
		},
		components: {
			uniRate
		},
		onLoad(obj) {
			console.log(obj)
			uni.request({
				url: `http://t.yushu.im/v2/movie/subject/${obj.id}?apikey=0df993c66c0c636e29ecbb5344252a4a`,
				success: (res) => {
					console.log(res)
					this.datalist = res.data
				}
			})
			// this.title=obj.title
		},
		methods: {
		}
	}
</script>

<style lang="less" scoped>
	page {
		width: 100%;
		height: 100%;
		.detail {
			width: 100%;
			height: 100%;
			display: flex;
			flex-direction: column;
			padding: 10px;
			box-sizing: border-box;
			background-color: #f4f4f4;

			.detailmsg {
				width: 720rpx;
				height: 150px;
				display: flex;
				margin-bottom: 20px;

				.left {
					width: 150px;
					height: 150px;

					.leftmsg {
						width: 100%;
						height: 100%;
					}
				}

				.right {
					margin-left: 20px;

					.righttitle {
						font-size: bold;
						font-size: 20px;
					}

					.moviecate {
						font-size: 12px;
						color: #fff;
						margin-bottom: 10px;
					}

					.clickbtn {
						width: 220px;
						height: 35px;
						font-size: 14px;
						display: flex;
						justify-content: space-around;

						.clickbtnone {
							border-radius: 12px;
							text-align: center;
							line-height: 35px;
							width: 100px;
							height: 35px;
							background-color: #fff;

							.msgset {
								width: 18px;
								height: 18px;
								margin-right: 10px;
							}
						}

						.clickbtntwo {
							background-color: #fff;
							border-radius: 12px;
							text-align: center;
							line-height: 35px;
							width: 100px;
							height: 35px;

							.msgset {
								width: 18px;
								height: 18px;
								margin-right: 10px;
							}
						}

					}
				}
			}

			.ratemsg {
				display: flex;
				flex-direction: column;
				padding: 10px;
				box-sizing: border-box;
				height: 150px;
				background-color: #fff;
				width: 720rpx;

				.ratetitle {
					font-size: 12px;
					color: #ddd;
					display: flex;
					justify-content: space-between;
				}

				.startrate {
					display: flex;
					justify-content: center;
					align-items: center;
					margin: auto;

					.left {
						display: flex;
						flex-direction: column;
						font-size: 30px;

						.start {
							margin-top: 20px;
						}
					}

					.right {
						display: flex;

						.leftdis {
							margin-bottom: 5px;
						}

						.rightdis {
							margin-left: 10px;

							.box {
								width: 100px;
								height: 6px;
								background-color: #fff888;
								margin-bottom: 5px;
							}

							.boxrate {
								font-size: 12px;
								align-self: flex-end;
							}
						}
					}
				}

			}

		}

		.moviemsg {
			margin-top: 10px;

			.titleproduce {
				font-size: 20px;
				font-weight: bold;
			}
		}

		.moviepeopel{
			height: 200px;

			.title {
				height: 30px;
				font-size: 20px;
				font-weight: bold;
			}
    .scrollmsg{
		width: 100%;
	  white-space: nowrap;
	.actor {
		display: inline-block;
		height: 150px;
	   display: flex;
		.actormsg {
			margin-right: 15px;
			display: flex;
			flex-direction: column;
			.imgs {
				width: 80px;
				height: 80px;
			}
			.imgsname{
				width: 80px;
				white-space: nowrap;
				overflow: hidden;
				text-overflow:ellipsis;
			}
		}
	}
}
		
		}
	}
</style>
