<template>
	<div class="ly_header">
		<div class="bl_header bl_header_clr">
			<p @click="change(0)" :class="[btnCheck==0? 'el_btn_is':'el_btn_def']">My Profile</p>
			<p @click="change(1)" :class="[btnCheck==1? 'el_btn_is':'el_btn_def']">Portraito</p>
			<p @click="change(2)" :class="[btnCheck==2? 'el_btn_is':'el_btn_def']">Star Bucks</p>
			<p @click="change(3)" :class="[btnCheck==3?'el_btn_is':'el_btn_def']">Japan</p>
			<p @click="change(4)" :class="[btnCheck==4? 'el_btn_is':'el_btn_def']">Contact</p>
		</div>
	</div>
</template>

<script>
export default {
	data(){
		return{
			tabState:0,
			btnCheck:0
		}
	},
	methods: {
		change(num){
			if(num == 0)
			{
				this.btnCheck = 0
				this.$emit('change')
			}
			else if(num ==1)
			{
				this.btnCheck = 1
				this.$emit('change01')
			}
				else if(num ==2)
			{
				this.btnCheck = 2
				this.$emit('change02')
			}
				else if(num ==3)
			{
				this.btnCheck = 3
				this.$emit('change03')
			}
				else if(num ==4)
			{
				this.btnCheck = 4
				this.$emit('change04')
			}
		},
	}
}
</script>

<style lang="scss" scoped>
.ly_header {
	position: absolute;
	right: 1%;
	top: 1%;
	z-index: 10;
}
.bl_header {
	box-sizing: border-box;
	height: 10%;
}
p{
	border: none;
	outline: none;
	margin: 0 5px;
}
.el_btn_is{
	display: inline-block;
	border-radius: 2%;
	padding: 5px 5px;
	margin: 0;
	border-top: none;
	box-shadow:  none;
}
.el_btn_def{
	display: inline-block;
	border-radius: 2%;
	padding: 5px 5px;
	margin: 0;
	box-shadow:  0 1px 1px 1px rgba(0, 0, 0, 0.29);
}

.bl_header_clr {
}
.el_btn{
	display: inline;
	outline: none;
}

.el_btn:active {
  transform: scale(0.8);
}
.el_btn:is {
	color: red;
}
</style>