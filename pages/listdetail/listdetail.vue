<template>
	<view class="content">
		<view class="hotmovie">
		<scroll-view class="hotmovielist" scroll-x>
				<view v-for="item in movielist" :key="item.id" class="listbox">
					<image :src="item.images.large" class="imgmsg"></image>
					<view class="title">{{item.title}}</view>
					<view class="movierating">
						<uni-rate  :margin="2" :size="12" :value="4"/>
						<text style="font-size:14px">{{item.rating.average}}</text>
					</view>
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	import {uniRate} from '@dcloudio/uni-ui'
	export default {
		data() {
			return {
             movielist:[],
			 ids:"",
			 start:1,
			 count:13
			}
		},
		onLoad(obj) {
			
			console.log(obj)
			let {
				id,
				start,
				count
			} = obj
			this.ids=obj.id
        this.getmovie();
		},
		methods: {
         getmovie(){
			 uni.showLoading({
			     title: '页面拼命加载中'
			 });
			 uni.request({
			     url: `http://t.yushu.im/v2/movie/${this.ids}`,
				 data: {
				 		apikey: '0df993c66c0c636e29ecbb5344252a4a',	//key认证
				 		start: this.start,	//从第一个索引开始获取数据
				 		count: this.count	//每页显示条数
				 					},
			     success: (res) => {
					  uni.hideLoading();
			 		  this.movielist=this.movielist.concat(res.data.subjects)
			 		  console.log(res.data.subjects[0].rating.average)
			     }
			 });
		 },
		},
		components: {uniRate},
		onReachBottom(){
			this.start=this.start+this.count
			this.getmovie()
			}}
</script>

<style lang="less" scoped>
	.content {
		height: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		.hotmovie{
			height:100%;
			width: 750rpx;
			padding: 10px;
			box-sizing: border-box;
			.hotmovielist{
				width: 750rpx;
				// white-space: nowrap;
				padding:10px 0px;
				box-sizing:border-box;
				height: 100%;
				.listbox{
					display: inline-block;
					width: 115px;
					height: 135px;
					margin-right: 10px;
					margin-bottom: 10px;
					.imgmsg{
						width: 120px;
						height: 100px;
					}
					.movierating{
						display: flex;
						justify-content: space-between;
					}
					.title{
						width: 120px;
						white-space: nowrap;
						overflow: hidden;
						text-overflow:ellipsis;
					}
				}
			}
		}
		
	}
</style>
