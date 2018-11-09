<template>
	<div>
		<div id="totalRate">
			<div id="rateConLeft">
				<span id="shopPoint">4.8</span>
				<span id="shopRating">商家评分</span>
				<img id="stars" src="../assets/stars.png" alt="" />
			</div>
			<div id="rateConRight">
				<div>
					<p class="ratingDetails">味道</p>
					<span class="ratingPoints">4.8</span>
				</div>
				<div style="margin-left:-10%;">
					<p class="ratingDetails">包装</p>
					<span class="ratingPoints">4.8</span>
				</div>
				<div>
					<p class="ratingDetails">配送</p>
					<span class="ratingPoints">4.9</span>
				</div>
			</div>
		</div>
		<div style="background:rgba(0,0,0,0.1);height:1vh;"></div>
		<ul id="tags">
			<li class="tag">全部 1000</li>
			<li class="tag">满意 100</li>
			<li class="tag">不满意 200</li>
			<li class="tag">有图 200</li>
			<li class="tag">味道好 201</li>
			<li class="tag">物美价廉 212</li>
			<li class="tag">不好吃 212</li>
			<li class="tag">送货慢 100</li>
			<li class="tag">分量一般 121</li>
			<li class="tag">分量足 312</li>
		</ul>
		<div @click="comment4">
			<svg slot="icon" viewBox="0 0 20 20" width="15" height="15" style="float:left;margin-left:3vw;">
				<path :class="commentFilter?'isChoosed':''" fill="lightgray" d="M17.595 3.494A9.978 9.978 0 0 0 10 0C4.477 0 0 4.477 0 10s4.477 10 10 10 10-4.477 10-10c0-1.631-.39-3.171-1.083-4.532l-9.973 9.608-4.715-4.714 1.653-1.653 3.062 3.062 8.65-8.277z"></path>
			</svg>
			<span style="font-size:12px;float:left;margin-left:1vw;line-height:16px;">只看有内容的评价</span>
		</div><br />
		<ul v-infinite-scroll="loadMore" infinite-scroll-disabled="loading" infinite-scroll-distance="10" infinite-scroll-immediate-check="true">
			<li v-for="item in list">
				<div class="commentCon">
					<div class="commentHead">
						<span class="userHead"></span>
					</div>
					<div class="commentBlock">
						<span class="comment_userName">这里是用户名（匿名）</span>
						<span class="comment_time">这里是系统时间</span><br />
						<div style="line-height:17px;margin-top:5px;margin-bottom:10px;">
							<img style="float:left" src="../assets/stars.png" alt="" /><span class="comment_rate">这里是评价</span>
						</div>
						<p class="comment_detail">太多了，老板我吃不完。太多了，老板我吃不完。太多了，老板我吃不完。太多了，老板我吃不完。</p>
						<img src="../assets/commentPic.png" alt="" />
					</div>
				</div>
			</li>
		</ul>
		<div style="padding-bottom:5%;">
			<mt-spinner type="triple-bounce" color="#00ccff" :size="20" v-show="this.loading"></mt-spinner>
		</div>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				commentFilter: false,
				loading: false,
				list: [],
			}
		},
		methods: {
			comment4() {
				this.commentFilter = !this.commentFilter
			},
			loadMore() { 
				this.loading = true
				setTimeout(() => {
					let last = this.list[this.list.length - 1] || 1;      
					for(let i = 1; i <= 5; i++) {        
						this.list.push(last + i); 
						this.loading = false   
					} 
				}, 2000)  
			},
		},
		mounted() {
			this.loadMore();
		}
	}
</script>

<style>
	#tags {
		display: flex;
		flex-wrap: wrap;
		justify-content: base;
	}
	
	.tag {
		width: 23%;
		height: 30px;
		background: #ebf5ff;
		margin-bottom: 2%;
		margin-right: 1vw;
		display: inline-block;
		font-size: 12px;
		line-height: 30px;
	}
	
	#totalRate {
		width: 100vw;
		height: 13vh;
		display: flex;
		justify-content: space-between;
	}
	
	#rateConLeft {
		flex: .4;
		line-height: 12vh;
		position: relative;
		vertical-align: middle;
	}
	
	#rateConRight {
		flex: .6;
		display: flex;
		justify-content: space-around;
		margin-top: 1vh;
	}
	
	#shopPoint {
		font-size: 38px;
		font-weight: bold;
		color: orangered;
		/*		margin-top:11px;*/
		display: inline-block;
	}
	
	#shopRating {
		font-size: 13px;
		color: #666;
		float: right;
		margin-top: -1vh;
		margin-right: 7vw;
		display: inline-block;
	}
	
	#stars {
		position: absolute;
		top: 7vh;
		right: 4vw
	}
	
	.ratingDetails {
		font-size: 13px;
	}
	
	.ratingPoints {
		font-size: 20px;
	}
	
	.isChoosed {
		fill: limegreen;
	}
	.commentCon{
		width:98%;
		margin-bottom:2vh;
		display: flex;
		height:100%;
	}
	.commentHead{
		flex:0.15;
		height:100%;
		padding-top:4px;
		margin-left:-20px;
	}
	.commentBlock{
		padding:0;
		flex:0.85;
		height:100%;
		text-align:left;
		
	}
	.userHead{
		width:40px;
		height:40px;
		border-radius:50%;
		background:lightblue;
		display:block;
	}
	.comment_userName{
		font-size:14px;
	}
	.comment_time{
		float:right;
		font-size:14px;
	}
	.comment_rate{
		font-size:12px;
		color:orangered;
	}
	.comment_detail{
		margin-top:0;
	/*	text-align: left;*/
		font-family:none;
		text-align:left;
		text-indent: 2.1em;
		
		
	}
</style>