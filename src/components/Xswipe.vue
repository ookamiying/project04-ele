<template>
	<mt-swipe :auto="0" id="swipeCon" :stopPropagation="false">
		<mt-swipe-item class="swipeItem">
			<div style="display:flex;justify-content: space-around;flex-wrap: wrap;">
				<div class="Items">
					<img src="../assets/swipe1.png" alt="" width="60" height="60" /><br />
					<span>美食</span>
				</div>
				<div class="Items">
					<img src="../assets/swipe2.png" alt="" width="60" height="60" /><br />
					<span>商超便利</span>
				</div>
				<div class="Items">
					<img src="../assets/swipe3.png" alt="" width="60" height="60" /><br />
					<span>水果</span>
				</div>
				<div class="Items">
					<img src="../assets/swipe4.png" alt="" width="60" height="60" /><br />
					<span>早餐</span>
				</div>
				<div class="Items">
					<img src="../assets/swipe5.png" alt="" width="60" height="60" /><br />
					<span>医疗健康</span>
				</div>
				<div class="Items">
					<img src="../assets/swipe6.png" alt="" width="60" height="60" /><br />
					<span>浪漫鲜花</span>
				</div>
				<div class="Items">
					<img src="../assets/swipe7.png" alt="" width="60" height="60" /><br />
					<span>厨房生鲜</span>
				</div>
				<div class="Items">
					<img src="../assets/swipe8.png" alt="" width="60" height="60" /><br />
					<span>跑腿代购</span>
				</div>
				<div class="Items">
					<img src="../assets/swipe9.png" alt="" width="60" height="60" /><br />
					<span>地方小吃</span>
				</div>
				<div class="Items">
					<img src="../assets/swipe10.png" alt="" width="60" height="60" /><br />
					<span>签到领红包</span>
				</div>
			</div>
		</mt-swipe-item>
		<!--		<mt-swipe-item class="swipeItem">
			<div style="display:flex;justify-content: space-between;flex-wrap: wrap;">
				<img src="../assets/100x100.png" alt="" width="80" height="80"/>
				<img src="../assets/100x100.png" alt="" width="80" height="80"/>
				<img src="../assets/100x100.png" alt="" width="80" height="80"/>
				<img src="../assets/100x100.png" alt="" width="80" height="80"/>
				<img src="../assets/100x100.png" alt="" width="80" height="80"/>
				<img src="../assets/100x100.png" alt="" width="80" height="80"/>
				<img src="../assets/100x100.png" alt="" width="80" height="80"/>
				<img src="../assets/100x100.png" alt="" width="80" height="80"/>
				<img src="../assets/100x100.png" alt="" width="80" height="80"/>
				<img src="../assets/100x100.png" alt="" width="80" height="80"/>
			</div>
		</mt-swipe-item>-->
		<mt-swipe-item class="swipeItem">
			<div style="display:flex;">
				<div class="Items">
					<img src="../assets/swipe11.png" alt="" width="60" height="60" /><br />
					<span>地方菜系</span>
				</div>
				<div class="Items">
					<img src="../assets/swipe12.png" alt="" width="60" height="60" /><br />
					<span>麻辣烫</span>
				</div>
			</div>
		</mt-swipe-item>
	</mt-swipe>
</template>

<script>
</script>

<style>
	.swipeItem {
		width: 200px;
		height: 200px;
		background: #FFF;
	}
	
	#swipeCon {
		width: 100%;
		height: 200px;
	}
	
	.Items {
		width: 70px;
		font-size: 12px;
		text-align: center;
	}
	.mint-swipe-indicator{
		background:gray !important;
		border-radius:0 !important;
		height:2px !important;
		width:15px !important;
	}
	.mint-swipe-indicators .is-active{
		background:darkblue !important;
	}
</style>