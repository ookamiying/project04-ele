<template>
	<div>
		<mt-header title="测试">
			<router-link to="/" slot="left">
				<mt-button icon="back">返回</mt-button>
			</router-link>
			<mt-button icon="more" slot="right"></mt-button>
		</mt-header>
	</div>
</template>

<script src="https://unpkg.com/mint-ui/lib/index.js"></script>
<script>
	export default {
		name: 'Xheader',
	}
</script>

<style>
	@import 'https://unpkg.com/mint-ui/lib/style.css';
</style>