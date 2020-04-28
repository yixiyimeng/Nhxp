<template>
	<mescroll-body ref="mescrollRef" @init="mescrollInit" @down="downCallback" @up="upCallback">
		<articleitem v-for="(item,index) in dataSource" :key="index"></articleitem>
	</mescroll-body>
</template>

<script>
	import articleitem from '@/components/articleitem.vue'
	import MescrollMixin from "@/components/mescroll-uni/mescroll-mixins.js";
	export default {
		mixins: [MescrollMixin], 
		data() {
			return {
				dataSource:10
			};
		},
		components:{
			articleitem
		}
	}
</script>

<style lang="scss">

</style>
