<template>
  <div class="ly_popup">
				<div v-if="num==4" class="bl_part_l"> 
					<div class="bl_pop_img_l">
						<img  class="el_popImg01" :src="popImg01">
					</div>
					<div class="bl_pop_txt_r">
						<h1>--  PoryRaito --</h1>
					</div>
				</div>
				<div v-if="num==3" class="bl_part_r"> 
					<div class="bl_pop_txt_r">
						<h1>--  PoryRaito --</h1>
					</div>
					<div class="bl_pop_img_l">
						<img  class="el_popImg01" :src="stbImg01">
					</div>
				</div>
				<div v-if="num==2" class="bl_part_l"> 
					<div class="bl_pop_img_l">
						<img  class="el_popImg01" :src="jpImg01">
					</div>
					<div class="bl_pop_txt_r">
						<h1>--  PoryRaito --</h1>
					</div>
				</div>
				<div v-if="num==1" class="bl_part_r"> 
					<div class="bl_pop_txt_r">
						<h1>--  PoryRaito --</h1>
					</div>
					<div class="bl_pop_img_l">
						<img  class="el_popImg01" :src="popImg01">
					</div>
				</div>
		<transition name="fade">
			<div v-if="num==0" class="bl_port">
				<img  class="a" :src="mainImg01">
				<button @click="isOff()" class="el_popTxt_last">Start</button>
			</div>
		</transition>
	</div>
</template>

<script>
export default {
  data() {
		return {
			num:4,
			number:false,
			popImg01: require('@/assets/portraiot01.png'),
			stbImg01: require('@/assets/stb01.png'),
			jpImg01: require('@/assets/japan01.png'),
			mainImg01: require('@/assets/main.png'),

		}
	},
	mounted() {
		setInterval(() => this.countdown(), 1500);
	},
	methods: {
		countdown() {
		if (this.num !== 0){
			this.num = this.num-1
		}else if(this.num == 1){
			clearInterval(this.countdown)
			this.number = true
			this.$emit('cha')
		}
		},
		isOff(){
			this.$emit('cha')
		}
	},
	computed: {

	}
}
</script>


<style lang="scss" scoped>
.fade-enter-active,.fade-leave-active {
  transition: all 3s ease;
}
.fade-enter {
	opacity: 0;
}
.fade-enter-to{
	opacity: 1;
}
.fade-leave{
  opacity: 1;
}
.fade-leave-to {
	opacity: 0;
}
.ly_popup {
	position: absolute;
	top: 0;
	left: 0;
	height: 100vh;
	width: 100vw;
	background: grey;
}

.bl_part_l {
	display: flex;
	position: absolute;
	align-items: center;
	left: 0;
	margin: 5%;
	width: 50%;
}
.el_popImg01{
	width: 500px;
	height:500px;
}
.bl_pop_img_l{
	margin: 2%;
}
.bl_pop_txt_r{
}
.bl_part_r {
	display: flex;
	position: absolute;
	align-items: center;
	right: 0;
	margin: 5%;
	width: 50%;
}
.el_popImg_last {
	width: 100%;
	height: auto;
}
.el_popTxt_last{
	position:absolute;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
	text-align: center;
}
.bl_port {
	height: 100vh;
}
.a{
	height: 100vh;
	width: 100%;
}
</style>
