<template>
  <div class="ly_popup">
		<div class="bl_popup">
				<div v-if="num==4" class="bl_part01"> 
					<div>
						<img  class="el_popImg" :src="popImg01">
					</div>
					<div class="bl_MyProfile_r">
						<h1>--  PoryRaito --</h1>
						<p>趣味で写真取ってます。<br>フジフィルムを愛してます。カメラ歴9年</p>
					</div>
				</div>
				<div v-if="num==3" class="bl_part02"> 
					<div class="bl_MyProfile_r">
						<h1>-- Star Bucks --</h1>
						<p>趣味で写真取ってます。<br>フジフィルムを愛してます。カメラ歴9年</p>
					</div>
					<div>
						<img  class="el_popImg" :src="stbImg01">
					</div>
				</div>
			<div v-if="num==2" class="bl_part01"> 
					<div>
						<img  class="el_popImg" :src="jpImg01">
					</div>
					<div class="bl_MyProfile_r">
						<h1>--  Japan  --</h1>
						<p>趣味で写真取ってます。<br>フジフィルムを愛してます。カメラ歴9年</p>
					</div>
			</div>
			<div v-if="num==1" class="bl_part02">
					<div class="bl_MyProfile_r">
						<h1>ー  MyProfile  ー</h1>
						<p>趣味で写真取ってます。<br>フジフィルムを愛してます。カメラ歴9年</p>
					</div>
					<div>
						<img  class="el_popImg" :src="stbImg01">
					</div>
			</div>
			<div v-if="num==0" class="bl_port">
				<h1>Start</h1>
			</div>
				{{num}}
		</div>
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
			jpImg01: require('@/assets/japan01.png')

		}
	},
	mounted() {
		setInterval(() => this.countdown(), 1500);
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
.fade-enter-active,.fade-leave-active {
  transition: all 1s ease;
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
	background-color: grey;
}
.bl_part01 {
		display: flex;
		position: absolute;
		left: 0;
}
.bl_MyProfile {
		display: flex;
		margin: 10%;
		justify-content: center;
	}
.bl_MyProfile_l {
		width: 70%;
	}
.el_MyProfile_l {
		height: 500px;
		width: 80%;
}
.bl_MyProfile_r {
		text-align: center;
		width: 70%;
	}
.bl_part02 {
	display: flex;
		position: absolute;
		right: 0;
}
.el_popImg {
	margin: 10px;
	height: 50vh;
	padding: 2px;
	box-shadow: inset 0 0 15px 15px grey;
}
.el_popImg::after {
  position: absolute;
  content: '';
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  box-shadow: inset 0 0 15px 15px gray;
}
</style>
