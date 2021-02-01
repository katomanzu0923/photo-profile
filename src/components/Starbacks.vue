<template>
	<div class="ly">
		<div class="bl01">
			<div v-show="isShow" class="bl_pop">
				<div class="imge">
					<img class="imgf" type="button" @click="of()" :src="popphoto">
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
						<h5>その他の写真</h5>
						<p><img class="el_popImg_l" :src="photo_l" type="button" @click="cha_l()"></p>
						<p><img class="el_popImg_r" :src="photo_r" type="button" @click="cha_r()"></p>
					</div>
				</div>
			</div>
		</div>
		<div class="bl">
			<div class="bl_img">
				<span class="bl_img_ttl">北海道・東北</span>
				<img class="el_popImg" :src="photo" type="button" @click="chi()"><p class="el_img_ttl">{{Location}}</p>
				<div class="bl_circle">
					<div :class="[check === false? 'onCircle': 'circle']">1</div>
					<div :class="[check === false? 'circle': 'onCircle']">2</div>
				</div>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(0)">Back</button><button class="el_Btn" type="button" @click="chi(0)">詳細へ</button><button @click="isNext(0)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">関東</span>
				<img class="el_popImg" :src="photo01" type="button" @click="chi()"><p class="el_img_ttl">{{Location01}}</p>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(1)">Back</button><button class="el_Btn" type="button" @click="chi(1)">詳細へ</button><button @click="isNext(1)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">北信越</span>
				<img class="el_popImg" :src="photo02" type="button" @click="chi()"><p class="el_img_ttl">{{Location02}}</p>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(2)">Back</button><button class="el_Btn" type="button" @click="chi(2)">詳細へ</button><button @click="isNext(2)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">東海</span>
				<img class="el_popImg" :src="photo03" type="button" @click="chi()"><p class="el_img_ttl">{{Location03}}</p>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(3)">Back</button><button class="el_Btn" type="button" @click="chi(3)">詳細へ</button><button @click="isNext(3)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">関西</span>
				<img class="el_popImg" :src="photo04" type="button" @click="chi()"><p class="el_img_ttl">{{Location04}}</p>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(4)">Back</button><button class="el_Btn" type="button" @click="chi(4)">詳細へ</button><button @click="isNext(4)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">中国・四国</span>
				<img class="el_popImg" :src="photo05" type="button" @click="chi()"><p class="el_img_ttl">{{Location05}}</p>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(5)">Back</button><button class="el_Btn" type="button" @click="chi(5)">詳細へ</button><button @click="isNext(5)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">九州・沖縄</span>
				<img class="el_popImg" :src="photo06" type="button" @click="chi()"><p class="el_img_ttl">{{Location06}}</p>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(6)">Back</button><button class="el_Btn" type="button" @click="chi(6)">詳細へ</button><button @click="isNext(6)" class="el_btn">Next</button>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			check:false,
			isPart:0,
			isNum:0,
			isShow:false,
			popphoto:'',
			photo:require('@/assets/stbHKD01.png'),
			photo01:require('@/assets/stbKWG01.png'),
			photo02:require('@/assets/stbTYM01.png'),
			photo03:require('@/assets/stbFOD01.png'),
			photo04:require('@/assets/stbkobe02.png'),
			photo05:require('@/assets/stbkobe02.png'),
			photo06:require('@/assets/stbkobe02.png'),
			photo07:require('@/assets/stbkobe02.png'),
			photo08:require('@/assets/stbkobe02.png'),
			photo_l:require('@/assets/stbkobe02.png'),
			photo_r:require('@/assets/stbkobe02.png'),
			Body:'x-t2',
			Renzu:'10-24',
			State:'F4',
			Location:'函館ベイサイド店',
			Location01:'鐘つき通り店',
			Location02:'冠水公園店',
			Location03:'フライトオブドリーム店',
			CameraData:{
				Body:['x-t2','x-Pro2'],
				Renzu:['10-24','16-80'],
				State:['F4'],
				Location:[
				'函館ベイサイド店','弘前公園前店',
				'鐘つき通り店','上野公園店',
				'冠水公園店','武生中央公園',
				'フライトオブドリーム店','浜松城公園店'
				],
			},
			PhotoData:{
				stbHKDTHK: [
					require('@/assets/stbHKD01.png'),
					require('@/assets/stbHKD02.png'),
					require('@/assets/stbHKD03.png'),
					require('@/assets/stbHSK01.png'),
					require('@/assets/stbHSK02.png'),
					require('@/assets/stbHSK03.png'),
				],
				stbKNT: [
					require('@/assets/stbKWG01.png'),
					require('@/assets/stbKWG02.png'),
					require('@/assets/stbKWG03.png'),
					require('@/assets/stbUEN01.png'),
					require('@/assets/stbUEN02.png'),
					require('@/assets/stbUEN03.png')
				],
				stbHSE: [
					require('@/assets/stbTYM01.png'),
					require('@/assets/stbTYM02.png'),
					require('@/assets/stbTYM03.png'),
					require('@/assets/stbFKI01.png'),
					require('@/assets/stbFKI02.png'),
					require('@/assets/stbFKI03.png')
				],
				stbTOK: [
					require('@/assets/stbFOD01.png'),
					require('@/assets/stbFOD02.png'),
					require('@/assets/stbFOD03.png'),
					require('@/assets/stbHMM01.png'),
					require('@/assets/stbHMM02.png'),
					require('@/assets/stbHMM03.png')
				],
				stbKNK: [
					require('@/assets/stbkobe01.png'),
					require('@/assets/stbkobe02.png'),
					require('@/assets/stbkobe03.png')
				],
				stbCSK: [
					require('@/assets/stbkobe01.png'),
					require('@/assets/stbkobe02.png'),
					require('@/assets/stbkobe03.png')
				],
				stbKOK: [
					require('@/assets/stbkobe01.png'),
					require('@/assets/stbkobe02.png'),
					require('@/assets/stbkobe03.png')
				],
			},
		}
	},
	mounted:{
		ui(){
			this.photo = this.PhotoData.stbHKDTHK[0]
		}
  },
	methods:{
		chi(isPart){
			this.isShow = true
			if(isPart == 0){
				if(this.isNum == 0){
					this.popphoto = this.photo
					this.photo_l = this.PhotoData.stbHKDTHK[1]
					this.photo_r = this.PhotoData.stbHKDTHK[2]
				}else if(this.isNum == 3){
					this.popphoto = this.photo
					this.photo_l = this.PhotoData.stbHKDTHK[4]
					this.photo_r = this.PhotoData.stbHKDTHK[5]
				}
			}else if(isPart == 1){
				if(this.isNum == 0){
					this.popphoto = this.photo01
					this.photo_l = this.PhotoData.stbKNT[1]
					this.photo_r = this.PhotoData.stbKNT[2]
				}else if(this.isNum == 3){
					this.popphoto = this.photo01
					this.photo_l = this.PhotoData.stbKNT[4]
					this.photo_r = this.PhotoData.stbKNT[5]
				}
			}else if(isPart == 2){
				if(this.isNum == 0){
					this.popphoto = this.photo02
					this.photo_l = this.PhotoData.stbHSE[1]
					this.photo_r = this.PhotoData.stbHSE[2]
				}else if(this.isNum == 3){
					this.popphoto = this.photo02
					this.photo_l = this.PhotoData.stbHSE[4]
					this.photo_r = this.PhotoData.stbHSE[5]
				}
			}else if(isPart == 3){
				if(this.isNum == 0){
					this.popphoto = this.photo03
					this.photo_l = this.PhotoData.stbTOK[1]
					this.photo_r = this.PhotoData.stbTOK[2]
				}else if(this.isNum == 3){
					this.popphoto = this.photo03
					this.photo_l = this.PhotoData.stbTOK[4]
					this.photo_r = this.PhotoData.stbTOK[5]
				}
			}
		},
		isNext(isPart){
			if(isPart == 0){
				if(this.isNum == 0){
					this.isNum = 3
					this.Location = this.CameraData.Location[1]
					this.photo = this.PhotoData.stbHKDTHK[this.isNum]
					this.check = true
				}else if(this.isNum == 3){
					this.isNum = 0
					this.Location = this.CameraData.Location[0]
					this.photo = this.PhotoData.stbHKDTHK[this.isNum]
					this.check = false
				}
			}else if(isPart == 1){
				if(this.isNum == 0){
					this.isNum = 3
					this.Location01 = this.CameraData.Location[3]
					this.photo01 = this.PhotoData.stbKNT[this.isNum]
				}else if(this.isNum == 3){
					this.isNum = 0
					this.Location01 = this.CameraData.Location[2]
					this.photo01 = this.PhotoData.stbKNT[this.isNum]
				}
			}else if(isPart == 2){
				if(this.isNum == 0){
					this.isNum = 3
					this.Location02 = this.CameraData.Location[5]
					this.photo02 = this.PhotoData.stbHSE[this.isNum]
				}else if(this.isNum == 3){
					this.isNum = 0
					this.Location02 = this.CameraData.Location[4]
					this.photo02 = this.PhotoData.stbHSE[this.isNum]
				}
			}else if(isPart == 3){
				if(this.isNum == 0){
					this.isNum = 3
					this.Location03 = this.CameraData.Location[7]
					this.photo03 = this.PhotoData.stbTOK[this.isNum]
				}else if(this.isNum == 3){
					this.isNum = 0
					this.Location03 = this.CameraData.Location[6]
					this.photo03 = this.PhotoData.stbTOK[this.isNum]
				}
			}else if(isPart == 4){
				if(this.isNum == 0){
					this.isNum = 1
					this.photo04 = this.PhotoData.stbKNK[this.isNum]
				}else if(this.isNum == 1){
					this.isNum = 2
					this.photo04 = this.PhotoData.stbKNK[this.isNum]
				}else if(this.isNum == 2){
					this.isNum = 0
					this.photo04 = this.PhotoData.stbKNK[this.isNum]
				}
			}else if(isPart == 5){
				if(this.isNum == 0){
					this.isNum = 1
					this.photo05 = this.PhotoData.stbCSK[this.isNum]
				}else if(this.isNum == 1){
					this.isNum = 2
					this.photo05 = this.PhotoData.stbCSK[this.isNum]
				}else if(this.isNum == 2){
					this.isNum = 0
					this.photo05 = this.PhotoData.stbCSK[this.isNum]
				}
			}else if(isPart == 6){
					if(this.isNum == 0){
					this.isNum = 1
					this.photo06 = this.PhotoData.stbCSK[this.isNum]
				}else if(this.isNum == 1){
					this.isNum = 2
					this.photo06 = this.PhotoData.stbCSK[this.isNum]
				}else if(this.isNum == 2){
					this.isNum = 0
					this.photo06 = this.PhotoData.stbCSK[this.isNum]
				}
			}else if(isPart == 7){
				if(this.isNum == 0){
					this.isNum = 1
					this.photo07 = this.PhotoData.stbKOK[this.isNum]
				}else if(this.isNum == 1){
					this.isNum = 2
					this.photo07 = this.PhotoData.stbKOK[this.isNum]
				}else if(this.isNum == 2){
					this.isNum = 0
					this.photo07 = this.PhotoData.stbKOK[this.isNum]
				}
			}
		},
		isBack(isPart){
			if(isPart == 0){
				if(this.isNum == 0){
					this.isNum = 3
					this.Location = this.CameraData.Location[1]
					this.photo = this.PhotoData.stbHKDTHK[this.isNum]
					this.check = true
				}else if(this.isNum == 3){
					this.isNum = 0
					this.Location = this.CameraData.Location[0]
					this.photo = this.PhotoData.stbHKDTHK[this.isNum]
					this.check = false
				}
			}else if(isPart == 1){
				if(this.isNum == 0){
					this.isNum = 3
					this.Location01 = this.CameraData.Location[3]
					this.photo01 = this.PhotoData.stbKNT[this.isNum]
				}else if(this.isNum == 3){
					this.isNum = 0
					this.Location01 = this.CameraData.Location[2]
					this.photo01 = this.PhotoData.stbKNT[this.isNum]
				}
			}else if(isPart == 2){
				if(this.isNum == 0){
					this.isNum = 3
					this.Location02 = this.CameraData.Location[5]
					this.photo02 = this.PhotoData.stbHSE[this.isNum]
				}else if(this.isNum == 3){
					this.isNum = 0
					this.Location02 = this.CameraData.Location[4]
					this.photo02 = this.PhotoData.stbHSE[this.isNum]
				}
			}
			else if(isPart == 3){
				if(this.isNum == 0){
					this.isNum = 3
					this.Location03 = this.CameraData.Location[7]
					this.photo03 = this.PhotoData.stbTOK[this.isNum]
				}else if(this.isNum == 3){
					this.isNum = 0
					this.Location03 = this.CameraData.Location[6]
					this.photo03 = this.PhotoData.stbTOK[this.isNum]
				}
			}
		},
		cha_l(){
			let main = this.popphoto
			let l = this.photo_l
			this.popphoto = l
			this.photo_l = main
		},
		cha_r(){
			let main = this.popphoto
			let r = this.photo_r
			this.popphoto = r
			this.photo_r = main
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
	width: 100%;
	margin-top: 2%;
}
.box {
  width: 100px;
  height: 100px;
  background: #ffa500;
  border-radius: 50%;
}
.bl_img{
	position: relative;
	background: rgba(104, 104, 104, 0.082);
	border: dashed 2px navy;
	width: 30%;
	height: 60vh;
	margin: 1%;
	margin-top: 5%;
}
.bl::after {
    content: "";
    display: block;
    width: 30%;
		margin: 1%;
}
.bl_imgBtn{
  margin:  0 auto;
}
.el_popImg{

	width: 95%;
	height: 75%;
	margin: 2.5% 2.5%;
}
.el_popImg_l{
	position: absolute;
	right: 60%;
	width: 40%;
	height: 40%;
}
.el_popImg_r{
	position: absolute;
	right: 10%;
	width: 40%;
	height: 40%;
}
.bl_pop {
	position: absolute;
	z-index: 10;
	top: 0%;
	left: 0;
	width: 100%;
	height: 200%;
	background: rgba(128, 128, 128, 0.925);
	filter: blur(80%);
}
.bl_img_ttl{
	text-align: center;
	position: absolute;
  display: inline-block;
	width: 80%;
	top: -10%;
	left: 10%;
	font-size: 2rem;
}

.el_img_ttl{
	background: white;
	bottom: 7%;
	text-align: center;
	padding: 2px 0;
	width: 80%;
	left: 0;
  right: 0;
  margin: auto;
}
.bl_imgBtn{
	display: flex;
	justify-content: center;
}
.el_btn{
	display: block;
	margin: 0 5px;
}
.imgf{
	position: absolute;
	left: 0;
	top: 0;
	padding-right: 2.5%;
	margin: 5% 2.5%;
	z-index: 10;
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
.bl_circle {
		margin: auto;
		text-align: center;
}
.circle {
	display: inline-block;
    width: 20px;
    height: 20px; 
    background-color:rgba(0, 0, 128, 0.082);
    border-radius: 50%; 
    text-align: center;/* ←文字を左右に中央揃え */
    line-height: 20px;/* ←文字を上下に中央揃え */
		margin: 5px 10px;
}
.onCircle {
	display: inline-block;
    width: 20px;
    height: 20px; 
    background-color:rgba(0, 0, 128, 0.712);
    border-radius: 50%; 
    text-align: center;/* ←文字を左右に中央揃え */
    line-height: 20px;/* ←文字を上下に中央揃え */
		margin: 5px 10px;
}
</style>