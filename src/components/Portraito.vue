<template>
	<div ly_portraio>
		<div class="bl_MyProfile">
			<div>
				<img  class="el_popImg" :src="Photo">
			</div>
			<div class="bl_MyProfile_r">
				<h1>ー  機種名  ー</h1>
				<p>{{Body}}</p>
				<h2>使用レンズ</h2>
				<p>{{Renzu}}</p>
				<h3>状態</h3>
				<p>{{State}}</p>
			</div>
		</div>
		<div class="bl_Slide">
			<button @click="isChange01()">1</button>
			<button @click="isChange02()">2</button>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			Photo:[require('@/assets/portraiot01.png')],
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
		isChange01(){
			this.Photo = this.PhotoData.portraitoImg[0]
			this.Body = this.CameraData.Body[0]
			this.Renzu = this.CameraData.Renzu[1]
			this.State = this.CameraData.Detail[0]
		},
		isChange02(){
			this.Photo = this.PhotoData.portraitoImg[1]
			this.Body = this.CameraData.Body[1]
			this.Renzu = this.CameraData.Renzu[0]
			this.State = this.CameraData.Detail[0]
		}
	}
}
</script>

<style lang="scss" scoped>
.ly_portraio {
	height: 100vh;
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
.el_popImg {
	margin: 10px;
	height: 50vh;
}
</style>