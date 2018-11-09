<template>
	<div style="height:1040px">
		<!--		<img src="../assets/upperHeader.png" alt="" style="width:100%" @click="discountClick" />-->
		<div id="shopDetail">
			<div id="shopBg"></div>
			<img src="../assets/header.png" alt="" id="shopHeader" width="80" height="80" />
			<p id="shopName">这里是商铺名字</p>
			<p id="shopEtc">这里是评价、月销量和配送时间</p>
			<div id="coupon">这里是优惠券</div>
			<p id="discountTotal" @click="discountClick">这里是打折汇总</p>
			<p id="notice">这里是公告</p>
			<router-link to="/Mpage" slot="left" id="back">
				<mt-button icon="back"></mt-button>
			</router-link>
		</div>
		<mt-navbar id="buttonCon" v-model="selected" :class="buttonConFixed? 'isFixed':''">
			<mt-tab-item class="buttons" id="1" @click.native.prevent="active = 'tab-container1'">点餐</mt-tab-item>
			<mt-tab-item class="buttons" id="2" @click.native.prevent="active = 'tab-container2'">评价</mt-tab-item>
			<mt-tab-item class="buttons" id="3" @click.native.prevent="active = 'tab-container3'">商家</mt-tab-item>
		</mt-navbar>
		<div v-if="buttonConFixed" style="height:44px"></div>
		<div class="page-tab-container">
			<mt-tab-container class="page-tabbar-tab-container" v-model="active">
				<mt-tab-container-item id="tab-container1">
					<div id="sideNav">
						<p v-for="(n,index) in 9" :class="{active: top>=arr[index]&&top<=arr[index+1] }" @click="jump(index)">经典奶茶{{n}}</p>
					</div>
					<div id="foodsNav">
						<ul style="margin-left:-40px;" v-for="(i,index) in 9" class="d_jump">
							<p>好吃的{{i}}</p>
							<li v-for="n in 5" @click="handleClick">
								<!--<img src="../assets/foods.png" alt="" width="280"/>-->
								<div style="width:320px;height:104px;margin-bottom:7%;">
									<img src="../assets/item.jpg" alt="" width="104" height="104" style="float:left" />
									<span class="itemName" style="font-weight:bold;margin-left:3%;font-size:17px;">经典珍珠奶茶</span><br />
									<span class="itemRemark" style="font-size:12px;margin-left:3%;margin-top:2%;color:#AAA">黑珍珠</span><br />
									<span class="itemSales" style="font-size:12px;margin-left:3%;color:#AAA">月售285份&emsp;好评率100%</span><br /><br />
									<span class="itemPrice" style="font-size:15px;margin-left:3%">￥</span>&nbsp;<span class="itemPrice">0.01</span>
									<button id="add2Cart">
										<svg viewBox="0 0 44 44" class="cart-minus" width="25" height="25">
											<path fill="none" d="M0 0h44v44H0z"></path>
											<path fill-rule="evenodd" d="M22 0C9.8 0 0 9.8 0 22s9.8 22 22 22 22-9.8 22-22S34.2 0 22 0zm10 24h-8v8c0 1.1-.9 2-2 2s-2-.9-2-2v-8h-8c-1.1 0-2-.9-2-2s.9-2 2-2h8v-8c0-1.1.9-2 2-2s2 .9 2 2v8h8c1.1 0 2 .9 2 2s-.9 2-2 2z" clip-rule="evenodd"></path>
										</svg>
									</button>
									<!--</div>-->
									<!--cart-->
									<!--	<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="20" height="20" viewBox="0 0 512 512">
										<path d="M64 464c0-26.51 21.49-48 48-48s48 21.49 48 48c0 26.51-21.49 48-48 48-26.51 0-48-21.49-48-48zM384 464c0-26.51 21.49-48 48-48s48 21.49 48 48c0 26.51-21.49 48-48 48-26.51 0-48-21.49-48-48zM480 256v-192h-416c0-35.346-28.653-64-64-64v32c17.645 0 32 14.355 32 32l24.037 206.027c-14.647 11.729-24.037 29.75-24.037 49.973 0 35.347 28.654 64 64 64h384v-32h-384c-17.673 0-32-14.327-32-32 0-0.11 0.007-0.218 0.008-0.328l415.992-63.672z" fill="#000000" />
									</svg>-->
								</div>
							</li>
						</ul>
					</div>
					<!--<img src="../assets/cart.png" alt="" style="position:fixed;bottom:0;width:100%;left:0;z-index:999999999" />-->
					<div style="position:fixed;bottom:0;width:100%;height:75px;left:0;z-index:999999999;display:flex;flex-direction: column;">
						<p id="discountTips">满19减19元，满19减19元，满19减19元，满19减19元</p>
						<div id="cartCon">
							<div id="cart">
								<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="25" height="25" viewBox="0 0 512 512" @click="detailClose">
									<path d="M64 464c0-26.51 21.49-48 48-48s48 21.49 48 48c0 26.51-21.49 48-48 48-26.51 0-48-21.49-48-48zM384 464c0-26.51 21.49-48 48-48s48 21.49 48 48c0 26.51-21.49 48-48 48-26.51 0-48-21.49-48-48zM480 256v-192h-416c0-35.346-28.653-64-64-64v32c17.645 0 32 14.355 32 32l24.037 206.027c-14.647 11.729-24.037 29.75-24.037 49.973 0 35.347 28.654 64 64 64h384v-32h-384c-17.673 0-32-14.327-32-32 0-0.11 0.007-0.218 0.008-0.328l415.992-63.672z" fill="darkgray" />
								</svg>
							</div>
							<span id="itemList">未选购商品</span>
							<span id="balance">￥20 起送</span>
						</div>
					</div>
					<mt-popup v-model="popupVisible" position="bottom">
						<!--<img src="../assets/popup.png" alt="" height="665" />-->
						<div id="itemDetail">
							<img src="../assets/item.jpg" alt="" width="100%" />
							<div id="detailClose" @click="detailClose">
								<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="24" height="24" viewBox="0 0 24 24" class="foodpanel-closeIcon_3a1DT">
									<defs>
										<path id="a" d="M13.132 12l6.47-6.47a.75.75 0 0 0-1.061-1.06l-6.47 6.47-6.47-6.47a.75.75 0 0 0-1.06 1.06L11.01 12l-.072.071.071.071-6.47 6.47a.75.75 0 0 0 1.061 1.06l6.47-6.47 6.47 6.47a.75.75 0 0 0 1.06-1.06l-6.47-6.47.072-.07-.071-.072z"></path>
									</defs>
									<g fill="none" fill-rule="evenodd">
										<use fill="#fff" fill-rule="nonzero" xlink:href="#a"></use>
										<path d="M0 0h24v24H0z"></path>
									</g>
								</svg>
							</div>
							<p class="itemName" style="font-weight:bolder;margin-left:3%;font-size:20px;margin-bottom:-2%">经典珍珠奶茶</p>
							<p class="itemSales" style="font-size:12px;margin-left:3%;color:#AAA">月售285份&emsp;好评率100%</p>
							<span class="itemPrice" style="font-size:15px;margin-left:3%;">￥</span>&nbsp;<span class="itemPrice">0.01</span><br />
							<span class="itemRemark" style="font-size:12px;margin-left:3%;color:#AAA">黑珍珠</span>
							<button id="add2Cart" style="margin-top:-10%;margin-right:5%">
								<svg viewBox="0 0 44 44" class="cart-minus" width="25" height="25">
									<path fill="none" d="M0 0h44v44H0z"></path>
									<path fill-rule="evenodd" d="M22 0C9.8 0 0 9.8 0 22s9.8 22 22 22 22-9.8 22-22S34.2 0 22 0zm10 24h-8v8c0 1.1-.9 2-2 2s-2-.9-2-2v-8h-8c-1.1 0-2-.9-2-2s.9-2 2-2h8v-8c0-1.1.9-2 2-2s2 .9 2 2v8h8c1.1 0 2 .9 2 2s-.9 2-2 2z" clip-rule="evenodd"></path>
								</svg>
							</button>
						</div>
					</mt-popup>
					<mt-popup v-model="discountVisible" position="bottom">
						<img src="../assets/popup2.png" alt="" height="295" />
					</mt-popup>
				</mt-tab-container-item>
				<mt-tab-container-item id="tab-container2" style="padding-top:20px">
					<!--<mt-cell v-for="n in 5" title="评价"></mt-cell>-->
					<xcomment></xcomment>
				</mt-tab-container-item>
				<mt-tab-container-item id="tab-container3" style="padding-top:20px">
					<mt-cell v-for="n in 7" title="商家"></mt-cell>
				</mt-tab-container-item>
			</mt-tab-container>
		</div>
	</div>
</template>

<script>
	import Xcomment from '../components/Xcomment.vue'
	export default {
		data() {
			return {
				active: "tab-container1",
				n: 1,
				popupVisible: false,
				discountVisible: false,
				buttonConFixed: false,
				selected: "1",
				top: 0,
				arr:[],
				brr:[]
			}
		},
		methods: {
			detailClose() {
				this.popupVisible = false
			},

			handleScroll2() {
				// 得到页面滚动的距离
				let self = this
				let scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
				self.offsetTop = document.querySelector('#buttonCon').offsetTop;
				self.offsetHeight = document.querySelector('#buttonCon').offsetHeight;
				/*				console.log(scrollTop,this.offsetTop, this.offsetHeight)*/
				// 判断页面滚动的距离是否大于吸顶元素的位置
				self.buttonConFixed = scrollTop > (self.offsetTop - self.offsetTop + 293);
			},

			jump(n) {
				let jump = document.querySelectorAll('.d_jump')
				let total = jump[n].offsetTop - 30
				let foods = document.querySelector("#foodsNav")
				let distance = foods.scrollTop
				// 平滑滚动，时长500ms，每10ms一跳，共50跳
				let step = total / 100
				if(total > distance) {
					smoothDown()
				} else {
					let newTotal = distance - total
					step = newTotal / 100
					smoothUp()
				}

				function smoothDown() {
					if(distance < total) {
						distance += step　　　　　　　
						let foods = document.querySelector("#foodsNav")
						foods.scrollTop = distance
						setTimeout(smoothDown, 10)
					} else {
						foods.scrollTop = total
					}
				}

				function smoothUp() {
					if(distance > total) {
						distance -= step　　　　　　　
						let foods = document.querySelector("#foodsNav")
						foods.scrollTop = distance
						setTimeout(smoothUp, 10)
					} else {
						foods.scrollTop = total
					}
				}
			},
			handleClick() {
				this.popupVisible = true
			},
			discountClick() {
				this.discountVisible = true
			},
			getTop() {
				var theTop = document.querySelector("#foodsNav")
				this.top = theTop.scrollTop
/*				setInterval(function(){
					console.log(theTop.scrollTop)
				},1000)*/

		},
		getofst(){
				var food = document.querySelectorAll(".d_jump")

				for(let i = 0; i < food.length; i++) {
					/*console.log(food[i].offsetTop)*/
									this.arr.push(food[i].offsetTop-150);
				}
		}

		},
		mounted() {
			// handleScroll为页面滚动的监听回调
			// window.addEventListener('scroll', this.handleScroll2);
			/*this.getTop();*/
			window.onscroll = this.handleScroll2;
			this.$nextTick(function() {
				var doc = document.querySelector("#foodsNav")
				doc.addEventListener('scroll', this.getTop)
				this.getofst()
			})

		},
		destoryed() {
			// window.removeEventListener('scroll', this.handleScroll2);
			window.onscroll = null;
		},
		updated() {},
		components: {
			Xcomment
		},
		watch: {
			top() {
				if(this.top>this.arr[this.arr.length-1]){
					var p = document.querySelectorAll("#sideNav p");
					p.className="";
					p[p.length-1].className="active";
				}else if(this.top<this.arr[this.arr.length-1]){
					var p = document.querySelectorAll("#sideNav p");
					p[p.length-1].className="";
				}
			}
		}

	}
</script>

<style>
	#back {
		position: absolute;
		top: 0;
		left: 0
	}
	
	#discountTotal {
		margin: 0;
		padding: 0;
	}
	
	#notice {
		margin: 0;
		padding: 0;
	}
	
	#shopEtc {
		margin: 0;
		padding: 0;
		font-size: 12px;
		margin-bottom: 15px;
	}
	
	#shopName {
		margin: 0;
		padding: 0;
		font-size: 26px;
		font-weight: bolder;
		margin-bottom: 1%;
	}
	
	#coupon {
		background: ghostwhite;
		width: 30%;
		margin-left: 35%;
	}
	
	#shopHeader {
		margin-top: -25%;
	}
	
	#shopBg {
		height: 100px;
		background: lightgreen;
	}
	
	#shopDetail {
		height: 293px;
		width: 100%;
		background: lightcyan;
		position: relative;
		text-align: center;
	}
	
	#sideNav {
		float: left;
		margin-top: 1%;
		background: rgba(0, 0, 0, .05);
		max-width: 18vw;
		height: 100vh;
		overflow: auto;
	}
	
	#sideNav p {
		/*margin: 15px;*/
		margin-top: 0;
		margin-bottom: 0;
		text-align: center;
		line-height: 60px;
		font-size: 14px;
		vertical-align: middle;
		display: block;
		width: 90vw;
		height: 8%;
		max-width: 18vw;
		/*		border:1px solid #00008B*/
	}
	
	#foodsNav {
		height: 650px;
		width: 80%;
		float: right;
		margin-top: 1%;
		overflow-y: auto;
		text-align: left;
		padding-left: 2vw;
	}
	
	.isFixed {
		position: fixed;
		top: 0px;
		left: 0px;
		width: 100%;
		z-index: 9999
	}
	
	.itemPrice {
		font-size: 18px;
		color: red;
	}
	
	.cart-minus {
		float: right;
		margin-top: -2%;
		margin-right: 5%;
		fill: dodgerblue
	}
	
	#discountTips {
		font-size: 11px;
		background: lightgoldenrodyellow;
		flex: .3;
		margin-bottom: 0;
	}
	
	#cartCon {
		width: 100%;
		height: 100%;
		background: #444;
		flex: .7;
		position: relative;
	}
	
	#cart {
		background: rgba(0, 0, 0, .6);
		width: 50px;
		height: 50px;
		border-radius: 50%;
		box-sizing: border-box;
		line-height: 55px;
		margin-top: -15px;
		margin-left: 10px;
		/*		display:inline-block;*/
		border: 4px solid rgba(0, 0, 0, .1)
	}
	
	#itemList {
		font-size: 14px;
		float: left;
		margin-left: 18%;
		margin-top: -5%;
		display: inline-block;
		color: #CCC
	}
	
	#balance {
		display: inline-block;
		height: 100%;
		width: 100px;
		background: #333;
		position: absolute;
		top: 0;
		right: 0;
		line-height: 44px;
		font-weight: bolder;
		color: white;
		font-size: 17px;
	}
	
	#itemDetail {
		width: 100vw;
		height: 94vh;
		position: relative;
		text-align: left;
		z-index: 9999999
	}
	
	#detailClose svg {
		position: absolute;
		top: 2%;
		right: 2%;
		background: rgba(0, 0, 0, .4);
		border-radius: 50%;
	}
	
	#add2Cart {
		float: right;
		margin-top: -2%;
		outline: none;
		border: none;
		background: none;
	}
	.active{
		background:white;
	}
</style>