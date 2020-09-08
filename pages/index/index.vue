<template>
	<view class="content">
		 <view class="nav">
			<input class="searchmsg" placeholder="搜索" @input="onKeyInput"  @blur="blurmsg"/>
		</view>
		<view class="hotmovie" v-for="(v,i) in moviemsg" :key="v">
			<view class="hottitle">
				<text class="left">{{v.title}}</text>
				<text class="right"@tap="watchmore(i)">查看更多&gt</text>
			</view>
		<scroll-view class="hotmovielist" scroll-x>
				
					<view v-for="(item,index) in v.movielist" :key="index" class="listbox">
						<navigator  :url="`../detail/detail?id=${item.id}`">
						<image :src="item.images.large" class="imgmsg"></image>
						<view class="title">{{item.title}}</view>
						<view class="movierating">
							<uni-rate  :margin="2" :size="12" :value="4"/>
							<text style="font-size:14px">{{item.rating.average}}</text>
						</view>
						</navigator>
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
			 moviemsg:[
				{ id:0,title:"影院热映",movielist:[],url:"http://t.yushu.im/v2/movie/in_theaters?apikey=0df993c66c0c636e29ecbb5344252a4a&start=1&count=10"},
				{ id:1,title:"豆瓣热门",movielist:[],url:"http://t.yushu.im/v2/movie/coming_soon?apikey=0df993c66c0c636e29ecbb5344252a4a&start=1&count=10"},
				{ id:2,title:"近期热门剧集",movielist:[],url:"http://t.yushu.im/v2/movie/top250?apikey=0df993c66c0c636e29ecbb5344252a4a&start=1&count=10"},
				{ id:3,title:"近期热门综艺",movielist:[],url:"http://t.yushu.im/v2/movie/coming_soon?apikey=0df993c66c0c636e29ecbb5344252a4a"},
				{ id:4,title:"畅销图书",movielist:[],url:"http://t.yushu.im/v2/movie/in_theaters?apikey=0df993c66c0c636e29ecbb5344252a4a&start=1&count=10"},
				{ id:5,title:"热门单曲榜",movielist:[],url:"http://t.yushu.im/v2/movie/in_theaters?apikey=0df993c66c0c636e29ecbb5344252a4a&start=1&count=10"},
			 ],
			 datamsg:"",
			 msgs:"",
			 // inputValue:""
			}
		},
		onLoad() { 
		this.geturl()
		},
		methods: {
			  onKeyInput: function(event) {
			            this.inputValue = event.target.value
						
						console.log(this.inputValue)
			        },
			blurmsg: function(event) {
				         this.msgs=this.inputValue
						 uni.navigateTo({
						 	 url:`../searchpage/searchpage?msgs=${this.msgs}`
						 	})
						 console.log(this.msgs)
				      },	
			geturl(){	
				for(let v of this.moviemsg){
					this.getmovie(v.url,v.id)
				}
				console.log(this.movielist)
			},
         getmovie(urlmsg,id){
			 uni.request({
			     url: urlmsg,
			     success: (res) => {
			         this.moviemsg[id].movielist=res.data.subjects
			     }
			 }) 
		 },
		 
		 watchmore(index){
			 if(index==0){
				 uni.navigateTo({
				 				 url:"../listdetail/listdetail?id=in_theaters&start=0&count=10"
				 })
			 }else if(index==1){
				 uni.navigateTo({
				 				 url:"../listdetail/listdetail?id=coming_soon&start=0&count=10"
				 })
			 }else if(index==2){
				 uni.navigateTo({
				 				 url:"../listdetail/listdetail?id=top250&start=20&count=10"
				 })
			 }else if(index==3){
				 uni.navigateTo({
				 				 url:"../listdetail/listdetail?id=top250&start=1&count=10"
				 })
			 }else if(index==4){
				 uni.navigateTo({
				 				 url:"../listdetail/listdetail?id=top250&start=1&count=10"
				 })
			 }
			 
		 }
		},
		components: {uniRate}
	}
</script>

<style lang="less" scoped>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;

		.nav {
			width: 750rpx;
			background-color: yellow;
			height: 40px;
			display: flex;
			justify-content: center;
			align-items: center;
			.searchmsg{
				width: 720rpx;
				height: 32px;
				background: #fff;
				border-radius: 15px;
				text-align: center;
				line-height:32px;
			}
		}
		.hotmovie{
			height: 200px;
			width: 750rpx;
			padding: 10px;
			box-sizing: border-box;
			.hottitle{
				height: 30px;
				align-items: center;
				display: flex;
				justify-content: space-between;
				.left{
					font-weight: bold;
				}
				.right{
					color: green;
				}
			}
			.hotmovielist{
				width: 750rpx;
				white-space: nowrap;
				padding:10px 0px;
				box-sizing:border-box;
				height: 170px;
				.listbox{
					display: inline-block;
					width: 120px;
					height: 120px;
					margin-right: 10px;
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
						// padding: 5px;
					}
				}
			}
		}
		
	}
</style>
