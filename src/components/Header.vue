<template>
	<div class="ly_header">
		<div class="bl_header">
			<button @click="change()" class="el_btn">My Profile</button>
			<button @click="change01()" class="el_btn">Portraito</button>
			<button @click="change02()" class="el_btn">Japanese Photo</button>
			<button @click="change03()" class="el_btn">Star Bucks</button>
		</div>
	</div>
</template>

<script>
export default {
	data(){
		return{
			kari:0
		}
	},
	methods: {
		change(){
			this.$emit('change')
		},
		change01(){
			this.$emit('change1')
		},
		change02(){
			this.$emit('change02')
		},
		change03(){
			this.$emit('change03')
		}
	}
}
</script>

<style lang="scss" scoped>
.ly_header {
	background: chartreuse;
	width: 100
}
.bl_header {
	display: flex;
	justify-content: center;
	box-sizing: border-box;
}
.el_btn{
	display: inline;
	margin: 5px;
}
.el_btn:active {
  -webkit-transform: translateY(2px);
  transform: translateY(2px);
  border-bottom: none;
}
</style>