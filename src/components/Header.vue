<template>
	<header class="ly_header">
		<div class="bl_header bl_header_clr">
			<p @click="change(0)" :class="[btnCheck==0? 'el_btn_is':'el_btn_def']" v-on:mouseover="u(0)" v-on:mouseleave="out(0)">My Profile</p>
			<p @click="change(1)" :class="[btnCheck==1? 'el_btn_is':'el_btn_def']">Portraits</p>
			<p @click="change(2)" :class="[btnCheck==2? 'el_btn_is':'el_btn_def']">Star Bucks</p>
			<p @click="change(3)" :class="[btnCheck==3?'el_btn_is':'el_btn_def']">Japan Trip</p>
			<p @click="change(4)" :class="[btnCheck==4? 'el_btn_is':'el_btn_def']">Contact Me</p>
		</div>
	</header>
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
$breakpoints: (
	m: "only screen and (max-width: 980px)",
	pc: "only screen and (max-width: 1199px)",
);
@mixin media($breakpoint) {
	@media #{map-get($breakpoints, $breakpoint)} {
		@content;
	}
}
.ly_header {
	position: absolute;
	width: 100%;
	left: 0%;
	top: 0%;
	height: 5%;
	z-index: 10;
	@include media(m){
		font-size: 0.8rem;
	}
}
.bl_header {
	box-sizing: border-box;
	display: flex;
	justify-content: center;
	align-items: center;
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
	padding: 0;
	margin: 0;
	cursor:pointer;
}
.el_btn_is{
	display: inline-block;
	margin:  1% 1%;
	font-weight: bold;
	padding: 0 1%;
	border-left: 1px solid;
	border-right: 1px solid;
	border-top: 1px solid;
}
.el_btn_def{
	display: inline-block;
	margin:  1% 1%;
	color:rgba(0, 0, 0, 0.425);
	font-weight: bold;
	padding: 0 1%;
	border-left: 1px solid rgba(0, 0, 0, 0.425);
	border-right: 1px solid rgba(0, 0, 0, 0.425);
	border-bottom: 1px solid rgba(0, 0, 0, 0.425);
}

</style>