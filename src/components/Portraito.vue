<template>
	<div class="ly">
		<div class="bl01">
			<div v-show="isShow" type="button" @click="of()" class="bl_pop">
				<img class="imgf" :src="photo">
				<div class="r">
				<h1>ー  機種名  ー</h1>
				<p>{{Body}}</p>
				<h2>使用レンズ</h2>
				<p>{{Renzu}}</p>
				<h3>状態</h3>
				<p>{{State}}</p>
			</div>
			</div>
			<div class="el01">関西エリア</div>
		</div>
		<div class="bl">
			<div><img class="el_popImg" :src="PhotoData.portraitoImg[1]" type="button" @click="chi()"></div>
			<div><img class="el_popImg" :src="PhotoData.portraitoImg[1]" type="button" @click="chi02()"></div>
			<div><img class="el_popImg" :src="PhotoData.portraitoImg[1]"></div>
			<div><img class="el_popImg" :src="PhotoData.portraitoImg[1]"></div>
			<div><img class="el_popImg" :src="PhotoData.portraitoImg[1]"></div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			isShow:false,
			photo:'a',
			Body:'x-t2',
			Renzu:'10-24',
			State:'F4',
			PhotoData:{
				portraitoImg: [
					require('@/assets/portraiot01.png'),
					require('@/assets/stb01.png')
				],
			},
			CameraData:{
				Body:['x-t2','x-pro2'],
				Renzu:['10-24','16-80'],
				Detail:['F4'],
			},
		}
	},
	methods:{
		chi(){
			this.photo = this.PhotoData.portraitoImg[0]
			this.Body = this.CameraData.Body[0]
			this.Renzu = this.CameraData.Renzu[0]
			this.State = this.CameraData.Detail[0]
			this.isShow = true
		},
		chi02(){
			this.photo = this.PhotoData.portraitoImg[0]
			this.Body = this.CameraData.Body[1]
			this.Renzu = this.CameraData.Renzu[1]
			this.State = this.CameraData.Detail[0]
			this.isShow = true
		},
		of(){
			this.isShow = false
		}
	}
}
</script>

<style lang="scss" scoped>
.ly {
	height: 100%;
}
.bl {
	display: flex;
	flex-wrap:wrap;
	flex-direction: row;
	justify-content: space-around;
	margin: 10px;
	width: 100%;
}
.bl:after {
    content: "";
    display: block;
    width: 500px;
    height: 0;
}
.el_popImg{
	width: 500px;
	height: 400px;
}
.bl_pop {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100vh;
	background: rgba(128, 128, 128, 0.678);
	filter: blur(80%);
}
.imgf{
	position: absolute;
	left: 0;
	top: 0;
	margin: 5%;
	z-index: 3;
	width: 70%;
	height: 700px;
}
.r{
	position: absolute;
	right: 0;
	width: 20%;
	margin: 5% 0;
	
}
</style>