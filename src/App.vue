<template>
	<div id="app">
		<!--		<div id="nav">
			<router-link to="/">Home</router-link> |
			<router-link to="/about">About</router-link>
		</div>-->
		<transition name="transitionRouter">
			<router-view></router-view>
		</transition>
		<!--		<router-view/>-->
	</div>
</template>

<script>
	//import './assets/index.js'
</script>

<style>
	@import './assets/style.css';
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
	}
	
	.transitionRouter-enter-active,
	.transitionRouter-leave-active {
		transition: all 0.4s;
	}
	
	.transitionRouter-enter,
	.transitionRouter-leave {
		transform: translate3d(100%, 0, 0);
	}
</style>