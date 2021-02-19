<template>
  <div class="ly_popup">
		<div class="ly_pop_load" v-show="num >=4"> 
      <h3 class="el_load_txt">読み込み中</h3>
      <vue-loading type="spiningDubbles" color="rgba(29, 29, 29, 0.904)"  class="el_load_icn">読み込み中</vue-loading>
    </div>
		<div v-show="num==3" class="bl_part_l">
			<div class="bl_pop_img_l">
				<img  class="el_popImg01" :src="popImg01">
			</div>
			<div class="bl_pop_txt_r">
				<h1>--  PortRait --</h1>
			</div>
		</div>
		<div v-show="num==2" class="bl_part_r"> 
			<div class="bl_pop_txt_r">
				<h1>--  Star  Bucks --</h1>
			</div>
			<div class="bl_pop_img_l">
				<img  class="el_popImg01" :src="stbImg01">
			</div>
		</div>
		<div v-show="num==1" class="bl_part_c"> 
			<div class="bl_pop_img_l">
				<img  class="el_popImg01" :src="jpImg01">
			</div>
			<div class="bl_pop_txt_r">
				<h1>--  Japan  Trip --</h1>
			</div>
		</div>
		<transition name="first">
			<h2 v-show="up==1">Photo Gyaraly</h2>
		</transition>
		<transition name="first">
			<h2 v-show="up==2" type="button" @click="isOff()" class="el_pop_txt">Start</h2>
		</transition>
		<transition name="fade">
			<div v-show="num==0" class="bl_port">
				<img  class="a" :src="mainImg01">
			</div>
		</transition>
	</div>
</template>

<script>
import { VueLoading } from 'vue-loading-template'

export default {
  data() {
		return {
			up:0,
			up02:false,
			num:8,
			number:false,
			popImg01: require('@/assets/portraiot01.png'),
			stbImg01: require('@/assets/stbHSK01.png'),
			jpImg01: require('@/assets/japan01.png'),
			mainImg01: require('@/assets/topM.png'),

		}
	},
	components: {
      VueLoading
    },
	mounted() {
		setInterval(() => this.countdown(), 1500);
	},
	methods: {
		countdown() {
		if (this.num !== 0){
			this.num = this.num-1
			console.log(this.num)
		}else if(this.num == 0){
			clearInterval(this.countdown)
			this.number = true
			if(this.up == 0){
				this.up = 1
			}else if(this.up == 1){
				setTimeout(this.ofn,3000)
				console.log(this.up)
			}
		}
		},
		kari(){
			this.num +=1
		},
		ofn(){
			this.up = 2
		},
		isup(){
			this.up02 = true
		},
		closeUp(){
			this.up = false
		},
		isOff(){
			this.$emit('cha')
		}
	},
	
}
</script>


<style lang="scss" scoped>
h2{
	position: absolute;
	text-align: center;
	left: 0;
	right: 0;
	top: 10%;
	font-size: 2rem;
	margin:auto;
}
.el_pop_txt:hover{
	color: whitesmoke;
	border: 0.5px solid rgba(0, 0, 0, 0.26);
	background: rgba(49, 49, 49, 0.137);
	cursor: pointer;
}
.first-enter-active,.first-leave-active {
	transition: opacity 3s;
}
.first-enter,.first-leave-to {
	opacity: 0;
}

.second-enter-active,.second-leave-active {
	transition: opacity 3s;
}
.second-enter,.second-leave-to {
	opacity: 0;
}

.fade-enter{
	opacity: 1;
}
.fade-leave{
  opacity: 1;
}
.fade-leave-to {
	opacity: 0;
}


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
	background: rgba(255, 255, 255, 0.986);
	z-index: 100;
}

.ly_pop_load{
	position: relative;
	height: 100%;
	width: 100%;
	background: rgba(255, 255, 255, 0.986);
}


.el_load_txt{
	position: absolute;
	top       : 50%;
	left      : 50%;
	font-size: 1.5rem;
	transform : translate(-50%, -50%);
	color: rgba(10, 10, 10, 0.904);
}

.el_load_icn{
	position: absolute;
	top       : 45%;
	left      : 50%;
	transform : translate(-50%, -50%);
}


.bl_part_l {
	position: absolute;
	align-items: center;
	left: 0;
	width: 100%;
	height: 50%;
}
.el_popImg01{
	position: absolute;
	width: 100%;
	height:100%;
}
.bl_pop_img_l{
	margin: 2%;
}
.bl_pop_txt_r{
	text-align: center;
}
.bl_part_r {
	display: flex;
	position: absolute;
	align-items: center;
	right: 0;
	margin: 15%;
	margin-right: 1%;
	width: 70%;
}
.bl_part_c {
	display: flex;
	position: absolute;
	align-items: center;
	right: 0;
	margin: 15%;
	margin-top: 20%;
	width: 70%;
}
.bl_part_m {
	display: flex;
	position: absolute;
	align-items: center;
	right: 0;
	margin: 15%;
	width: 70%;
}
.el_popImg_last {
	width: 100%;
	height: auto;
	text-align: center;
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
.el_pop_txt{
	color: rgba(0, 0, 0, 0.555);
	border: 0.5px solid rgba(0, 0, 0, 0.26);
	width: 15%;
}
.a{
	height: 100vh;
	width: 100%;
}
</style>
