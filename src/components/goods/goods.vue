<template>
	<div class="goods">
		<div class="menu-wrapper"></div>
		<div class="foods-wrapper"></div>
	</div>

</template>

<script>
const ERR_OK = 0;
export default {
	data() {
		return {
			goods: []
		};
	},
	props: {
		seller: {
			type: Object
		}
	},
	created() {
		this.$http.get('/api/goods').then((response) => {
			response = response.body;
			if (response.errno === ERR_OK) {
				this.goods = response.data;
			}
		});
	}
};
</script>

<style lang="stylus">
.goods
	display flex
	position:absolute
	top 174px
	width 100%
	bottom 46px
	overflow hidden
	.menu-wrapper
		flex 0 0 80px
		width 80px
		background #f3f5f7
	.foods-wrapper
		flex 1

</style>