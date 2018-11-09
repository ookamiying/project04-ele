<template>
	<div>
		<Xheader></Xheader>
		<Xsearch></Xsearch>
		<Xtab></Xtab>
	</div>
</template>

<script>
		import Xheader from '../components/Xheader.vue'
		import Xsearch from '../components/Xsearch.vue'
		import Xtab from '../components/Xtab.vue'
		export default{
			name:"MPage",
			components:{
				Xheader,
				Xsearch,
				Xtab
			}
		}
</script>

<style>
</style>