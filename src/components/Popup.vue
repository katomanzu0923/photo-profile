<template>
  <div class="ly_popup">
		<div class="bl_popup">
				<div v-if="num==5" class="bl_port"> 
				<h1>Portraito</h1>
				<div><img src="@/assets/logo.png" alt=""></div>
				</div>
				<div v-if="num==4" class="bl_port"> 
				<h1>Japanese Photo</h1>
				<img src="@/assets/logo.png" alt="">
				</div>
				<div v-if="num==3" class="bl_port"> 
				<h1>Star Bucks</h1>
				<div><img src="@/assets/logo.png" alt=""></div>
			</div>
				<div v-if="num==2" class="bl_port"> 
				<h1>Japanese Culture</h1>
				<div><img src="@/assets/logo.png" alt=""></div>
			</div>
				<div v-if="num==1" class="bl_port"> 
					<h1>Happy Photo</h1>
					<div><img src="@/assets/logo.png" alt=""></div>
				</div>
				<div v-if="num==0" class="bl_port"> 
				<h1>Start</h1>
				<div><img src="@/assets/logo.png" alt=""></div>
				</div>
				<p>読み込み中</p>
				{{num}}
				<div v-if="num== 0">0</div><div v-if="num== 1">1</div><div v-if="num == 2">2</div><div v-if="num == 3">3</div><div v-if="num == 4">4</div><div v-if="num == 5">5</div>
			<button @click="ch()">s</button>
		</div>
	</div>
</template>

<script>
export default {
  data() {
		return {
			num:1,
			number:false,

		}
	},
	mounted() {
			setInterval(() => this.countdown(), 1700);
	},
	methods: {
		countdown() {
		if (this.num !== 0){
			this.num = this.num-1
		}else if(this.num == 0){
			clearInterval(this.countdown)
			this.number = true
			this.$emit('cha')
		}
		}
	},
	computed: {

	}
}
</script>


<style lang="scss" scoped>
.ly_popup {
	position: absolute;
	top: 0;
	left: 0;
	height: 100vh;
	width: 100vw;
	background-color: grey;
}
.bl_popup {
	border: 1px solid black;
	width: 50%;
	margin: 25%;
}
</style>
