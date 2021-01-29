<template>
	<div class="ly">
		<div class="bl01">
			<div v-show="isShow" class="bl_pop">
				<div class="imge">
					<img class="imgf" type="button" @click="of()" :src="photo">
				</div>
				<div>
					<div class="r">
						<h1>ー  機種名  ー</h1>
						<p>{{Body}}</p>
						<h2>使用レンズ</h2>
						<p>{{Renzu}}</p>
						<h3>状態</h3>
						<p>{{State}}</p>
						<h4>場所</h4>
						<p>{{Location}}</p>
						<button @click="isBack()" class="el_btn">Back</button><button @click="isNext()" class="el_btn">Next</button>
					</div>
				</div>
			</div>
		</div>
		<div class="bl">
			<div><img class="el_popImg" :src="PhotoData.stbkobe[0]" type="button" @click="chi()"></div>
			<div><img class="el_popImg" :src="PhotoData.stboki[0]" type="button" @click="chi02()"></div>
			<div><img class="el_popImg" :src="PhotoData.stboki[0]"></div>
			<div><img class="el_popImg" :src="PhotoData.stboki[0]"></div>
			<div><img class="el_popImg" :src="PhotoData.stboki[0]"></div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			isNum:'',
			isPart:'',
			isShow:false,
			photo:'a',
			Body:'x-t2',
			Renzu:'10-24',
			State:'F4',
			Location:'',
			PhotoData:{
				stbkobe: [
					require('@/assets/stb01.png'),
					require('@/assets/stbkobe02.png'),
					require('@/assets/stbkobe03.png')
				],
				stboki:[
					require('@/assets/stbok.png'),
					require('@/assets/stboki01.png'),
					require('@/assets/stboki02.png'),
					require('@/assets/stboki03.png')
				]
			},
			CameraData:{
				Body:['x-t2','x-pro2','iphone11'],
				Renzu:['10-24','16-80'],
				Detail:['F4'],
				Location:['神戸ビリケンタワー店舗','沖縄本町店']
			},
		}
	},
	methods:{
		chi(){
			this.isNum = 0
			this.isPart = 0
			this.photo = this.PhotoData.stbkobe[this.isNum]
			this.Body = this.CameraData.Body[0]
			this.Renzu = this.CameraData.Renzu[0]
			this.State = this.CameraData.Detail[0]
			this.Location = this.CameraData.Location[0]
			this.isShow = true
		},
		isNext(){
			if(this.isPart == 0){
				if(this.isNum == 0){
				this.isNum = 1
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stbkobe[this.isNum]
			}else if(this.isNum == 1){
				this.isNum = 2
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stbkobe[this.isNum]
			}else if(this.isNum == 2){
				this.isNum = 0
				this.Body = this.CameraData.Body[0]
				this.photo = this.PhotoData.stbkobe[this.isNum]
			}
			}else if(this.isPart == 1){
				if(this.isNum == 0){
				this.isNum = 1
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stboki[this.isNum]
			}else if(this.isNum == 1){
				this.isNum = 2
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stboki[this.isNum]
			}else if(this.isNum == 2){
				this.isNum = 3
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stboki[this.isNum]
			}else if(this.isNum == 3){
				this.isNum = 0
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stboki[this.isNum]
			}
			}
		},
		isBack(){
			if(this.isPart == 0){
				if(this.isNum == 0){
				this.isNum = 2
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stbkobe[this.isNum]
			}else if(this.isNum == 2){
				this.isNum = 1
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stbkobe[this.isNum]
			}else if(this.isNum == 1){
				this.isNum = 0
				this.Body = this.CameraData.Body[0]
				this.photo = this.PhotoData.stbkobe[this.isNum]
			}
			}else if(this.isPart ==1){
				if(this.isNum == 0){
				this.isNum = 3
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stbkoki[this.isNum]
			}else if(this.isNum == 3){
				this.isNum = 2
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stboki[this.isNum]
			}else if(this.isNum == 2){
				this.isNum = 1
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stbkoki[this.isNum]
			}else if(this.isNum == 1){
				this.isNum = 0
				this.Body = this.CameraData.Body[2]
				this.photo = this.PhotoData.stbkoki[this.isNum]
			}
			}
		},
		chi02(){
			this.photo = this.PhotoData.stboki[0]
			this.Body = this.CameraData.Body[1]
			this.Renzu = this.CameraData.Renzu[1]
			this.State = this.CameraData.Detail[0]
			this.Location = this.CameraData.Location[1]
			this.isShow = true
			this.isNum = 0
			this.isPart = 1
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
    width: 500px;  /* .boxに指定したwidthと同じ幅を指定する */
    height: 0;
}
.el_popImg{
	width: 500px;
	height: 400px;
}
.bl_pop {
	position: absolute;
	top: 0%;
	left: 0;
	width: 100%;
	height: 100vh;
	background: rgba(128, 128, 128, 0.925);
	filter: blur(80%);
}
.el_btn{
	margin: 0 5px;
}
.imgf{
	position: absolute;
	left: 0;
	top: 0;
	padding-right: 2.5%;
	margin: 5% 2.5%;
	z-index: 3;
	width: 70%;
	height: 700px;
	border-right: 1px dotted black;
}
.r{
	position: absolute;
	text-align: center;
	right: 0;
	width: 25%;
	margin: 5% 0;
	
}
</style>