<template>
	<div>
		<div  style="margin-bottom:50px;"> <!--style="height: 50vh;"-->
			<p>------推荐商家------</p>
			<ul  v-infinite-scroll="loadMore" infinite-scroll-disabled="loading" infinite-scroll-distance="10" infinite-scroll-immediate-check="true">
				<li v-for="item in list" >
					<!--<img src="../assets/test.png" alt="" width="330" height="135" @click="goList"/>-->
					<div class="shops" @click="goList">
						<img class="shopHead" src="../assets/header.png" alt="" width="80" height="80"/>
						<p class="shopTitle">这里是店铺名字哦</p>
						<p class="monthSales">rating和月销量</p>
						<span class="atLeast">起送|配送费</span><span class="cost">距离|耗时</span>
						<span class="tags">我是标签</span><br />
						<span>预留</span>
					</div>
				</li>
			</ul>
			<div style="padding-bottom:5%;">
				<mt-spinner type="triple-bounce" color="#00ccff" :size="20" v-show="this.loading"></mt-spinner>
			</div>
		</div>
	</div>
</template>

<script>
	export default { 
		 data() {  
			return {    
				loading: false,
				list: [],
			} 
		},
		  mounted() {    
			this.loadMore();  
		},
		  methods: {    
			loadMore() { 
				this.loading = true
				setTimeout(() => {
					let last = this.list[this.list.length - 1] || 1;      
					for(let i = 1; i <= 5; i++) {        
						this.list.push(last + i); 
						this.loading = false   
/*						this.$toast('加载成功！');  */
					} 
				}, 2000)  
			},
			goList(){
				/*console.log(e.target)*/
				this.$router.push({name:'list'})
				//if(e.target.nodeName=="li"){
				//console.log(11)
				//}
			}
		}
	}
</script>

<style>
	ul {
		list-style: none;
	}
	.shops{
		margin-left:-5%;
		width:100%;
		height:100px;
		margin-bottom:10px;
		text-align:left;
	}
	.shopHead{
		float:left;
		margin-right:2%;
	}
	.shopTitle{
		font-weight:bold;
		font-size:16px;
	}
	.monthSales{
		margin-top:-4%;
		font-size:12px;
		color:#333
	}
	.cost,.atLeast{
		margin-top:-3%;
		font-size:12px;
		color:#333
	}
	.cost{
		float:right;
	}
	.atLeast{
		float:left;
	}
	.tags{
		margin-left:-17%;
		font-size:12px;
	}
</style>