<template>
	<div>
		<mt-search  id="searchBar" cancel-text="取消" placeholder="搜索" style="height:52px;" :class="searchBarFixed? 'isFixed':''">
		</mt-search>
		<div v-if="searchBarFixed" style="height:52px"></div>
	</div>
	
	
</template>

<script>
	export default {
/*		model:{
			prop:"value"
		},*/
		data(){
			return{
				searchBarFixed:false
			}
		},
		mounted() {
			// handleScroll为页面滚动的监听回调
			// window.addEventListener('scroll', this.handleScroll);
			window.onscroll = this.handleScroll;
		},
		destoryed() {
			//window.removeEventListener('scroll', this.handleScroll);
			window.onscroll = null;
		},
		methods: {
			handleScroll() {
				// 得到页面滚动的距离
				let self = this
				let scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
				self.offsetTop = document.querySelector('#searchBar').offsetTop;
				self.offsetHeight = document.querySelector('#searchBar').offsetHeight;
/*				console.log(scrollTop,this.offsetTop, this.offsetHeight)*/
				// 判断页面滚动的距离是否大于吸顶元素的位置
				self.searchBarFixed = scrollTop > (self.offsetTop - self.offsetTop+36);
			},
//			handleScroll() {
//				var scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop
//				var offsetTop = document.querySelector('#searchBar').offsetTop+40
//				var qwe = document.querySelector('#searchBar').offsetTop
//				
//				if(scrollTop > offsetTop) {
//					this.searchBarFixed = true
//				} else if(scrollTop > qwe) {
//					this.searchBarFixed = false
//				}
//			},
		}
	}
</script>

<style>
	.isFixed {
		position: fixed;
		top: 0px;
		left: 0px;
		width:100%;
		z-index:9999
	}
	.mint-searchbar{
		background:#26a2ff !important;	}
	.mint-searchbar-cancel{
		color:#FFF !important;	}
</style>