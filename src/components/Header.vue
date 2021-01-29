<template>
	<div class="ly_header">
		<div class="bl_header bl_header_clr">
			<button @click="change()" class="el_btn">My Profile</button>
			<button @click="change01()" class="el_btn">Portraito</button>
			<button @click="change02()" class="el_btn">Star Bucks</button>
			<button @click="change03()" class="el_btn">Japan</button>
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
	width: 100%;
}
.bl_header {
	display: flex;
	justify-content: center;
	box-sizing: border-box;
	height: 10%;
}
.bl_header_clr {
	background: rgba(104, 104, 104, 0.082);
	border-bottom:rgba(0, 0, 128, 0.534) 1px solid;
}
.el_btn{
	display: inline;
	margin: 30px;
	outline: none;
}

.el_btn:active {
  transform: scale(0.8);
}
.el_btn:is {
	color: red;
}
</style>