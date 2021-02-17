<template>
	<div class="ly_header">
		<div class="bl_header bl_header_clr">
			<p @click="change(0)" :class="[btnCheck==0? 'el_btn_is':'el_btn_def']">My Profile</p>
			<p @click="change(1)" :class="[btnCheck==1? 'el_btn_is':'el_btn_def']">Portraito</p>
			<p @click="change(2)" :class="[btnCheck==2? 'el_btn_is':'el_btn_def']">Star Bucks</p>
			<p @click="change(3)" :class="[btnCheck==3?'el_btn_is':'el_btn_def']">Japan Trip</p>
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
	width: 100%;
	left: 0%;
	top: 0%;
	z-index: 10;
	height: 5%;
}
.bl_header {
	box-sizing: border-box;
	display: flex;
	justify-content: center;
	width: 100%;
	top: 0;
	left: 0;
	right: 0;
	height: 100%;
	background: rgba(236, 235, 235, 0.856);
	box-shadow:  0 1px 1px 1px rgba(0, 0, 0, 0.29);
}
p{
	border: none;
	outline: none;
}
.el_btn_is{
	display: inline-block;
	margin:  1% 2.5%;
	font-weight: bold;
}
.el_btn_def{
	display: inline-block;
	border-radius: 2%;
	margin:  1% 2.5%;
	color:rgba(0, 0, 0, 0.425);
	font-weight: bold;
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