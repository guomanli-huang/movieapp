<template>
	<view class="list"> 
		<div class="movielist">
			<view class="left">
				<image :src="datalist.images.large" class="leftmsg"></image>
			</view>
			<view class="right">
				<view class="title">{{datalist.title}}</view>
				<view>
					<uni-rate :max="5" :value="datalist.rating.average/2" :size="10" class="start" />
					<text>{{datalist.rating.average}}</text>
				</view>
				<view class="moviecate">剧情
					<text v-for="item in datalist.genres">{{item}}/</text>
					<text>{{datalist.countries}}/</text>
					<text>片长{{datalist.reviews_count}}分钟</text>
				</view>
			</view>
		</div>
	</view>
</template>

<script>
	import {
		uniRate
	} from '@dcloudio/uni-ui'
	export default {
		data() {
			return {
            datalist:{}
			}
		},
		components: {
			uniRate
		},
		methods: {

		},
		onLoad(obj) {
			console.log(obj)
			uni.request({
				url: `http://t.yushu.im/v2/movie/search?apikey=0df993c66c0c636e29ecbb5344252a4a&q=${obj.msgs}&start=0&count=10`,
				success: (res) => {
						this.datalist=res.data.subjects[0]
						console.log(this.datalist)
				}
			})
		}
	}
</script>

<style lang="less" scoped>
.list{
	height: 100%;
	width:100%;
	padding: 10px;
	box-sizing: border-box;
	display: flex;
	flex-direction: column;
	.movielist{
		
		display: flex;
		justify-content: space-between;
		.left{
			width: 140rpx;
			height: 100px;
			.leftmsg{
				width: 100%;
				height: 100%;
				margin-right: 10px;
			}
		}
		.right{
			margin-left: 10px;
			flex: 1;
			.title{
				font-size:18px ;
				font-weight: bold;
			}
			.moviecate{
				font-size: 14px;
			}
		}
	}
}
</style>
