<template>
	<div class="bl">
			<div class="bl_img">
				<img class="el_popImg" :src="photo">
				<img class="el_popImg01" :src="photo">
				<img class="el_popImg02" :src="photo">
				<img class="el_popImg03" :src="photo">
			</div>
		</div>
</template>

<script>
export default {
	data() {
		return {
			NumM:'',
			Numl:'',
			Numr:'',
			secNum:0,
			check:0,
			check01:0,
			check02:0,
			check03:0,
			isPart:0,
			isNum:0,
			isShow:false,
			popphoto:'',
			photo:require('@/assets/portWORKm.png'),
			photo01:require('@/assets/portGIRLm.png'),
			photo02:require('@/assets/portMENm.png'),
			photo03:require('@/assets/stbFOD01.png'),
			photo04:require('@/assets/stbKTN01.png'),
			photo05:require('@/assets/stbDGO01.png'),
			photo06:require('@/assets/stbOKW01.png'),
			photo_l:require('@/assets/stbkobe02.png'),
			photo_r:require('@/assets/stbOKW01.png'),
			popphoto_l:'',
			popphoto_r:'',
			Body:'x-t2',
			Renzu:'10-24',
			State:'F4',
			Location:'函館ベイサイド店',
			Location01:'鐘つき通り店',
			Location02:'冠水公園店',
			Location03:'フライトオブドリーム店',
			Location04:'北野異人館店',
			Location05:'道後温泉駅店',
			Location06:'沖縄本町店',
			CameraData:{
				Body:['x-t2','x-Pro2'],
				Renzu:['10-24','16-80'],
				State:['F4'],
				Location:[
				'函館ベイサイド店','弘前公園前店',
				'鐘つき通り店','上野公園店',
				'冠水公園店','武生中央公園',
				'フライトオブドリーム店','浜松城公園店',
				'二寧坂店','メリケンパーク店','北野異人館店',
				'道後温泉駅店','出雲大社店',
				'沖縄本町店','鹿児島店',
				],
			},
			PhotoData:{
				portWORK: [
					require('@/assets/portWORKm.png'),
				],
				stbGIRL: [
					require('@/assets/portGIRLm.png'),
				],
				portMEN: [
					require('@/assets/portMENm.png')
				],
			},
		}
	},
	mounted:{
		ui(){
			this.photo = this.PhotoData.portWORK[0]
		}
  },
	methods:{
		chi(isPart)
		{
			this.isShow = true
			if(isPart == 0)
			{
				if(this.isNum == 0)
				{
					this.popphoto = this.photo
					this.Body = this.CameraData.Body[0]
					this.Renzu = this.CameraData.Renzu[1]
					this.State = this.CameraData.State[0]
					this.photo_l = this.PhotoData.portWORK[1]
					this.photo_r = this.PhotoData.portWORK[2]
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 3)
				{
					this.popphoto = this.photo
					this.Body = this.CameraData.Body[1]
					this.Renzu = this.CameraData.Renzu[1]
					this.State = this.CameraData.State[0]
					this.photo_l = this.PhotoData.portWORK[4]
					this.photo_r = this.PhotoData.portWORK[5]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
					
				}
			}
			else if(isPart == 1)
			{
				if(this.isNum == 0)
				{
					this.popphoto = this.photo01
					this.photo_l = this.PhotoData.stbGIRL[1]
					this.photo_r = this.PhotoData.stbGIRL[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 3)
				{
					this.popphoto = this.photo01
					this.photo_l = this.PhotoData.stbGIRL[4]
					this.photo_r = this.PhotoData.stbGIRL[5]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
			}
			else if(isPart == 2)
			{
				if(this.isNum == 0)
				{
					this.popphoto = this.photo02
					this.photo_l = this.PhotoData.portMEN[1]
					this.photo_r = this.PhotoData.portMEN[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 3)
				{
					this.popphoto = this.photo02
					this.photo_l = this.PhotoData.portMEN[4]
					this.photo_r = this.PhotoData.portMEN[5]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
			}
			else if(isPart == 3)
			{
				if(this.isNum == 0)
				{
					this.popphoto = this.photo03
					this.photo_l = this.PhotoData.stbTOK[1]
					this.photo_r = this.PhotoData.stbTOK[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 3)
				{
					this.popphoto = this.photo03
					this.photo_l = this.PhotoData.stbTOK[4]
					this.photo_r = this.PhotoData.stbTOK[5]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
			}
			else if(isPart == 4)
			{
				if(this.isNum == 0)
				{
					this.popphoto = this.photo04
					this.photo_l = this.PhotoData.stbKNK[1]
					this.photo_r = this.PhotoData.stbKNK[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 4)
				{
					this.popphoto = this.photo04
					this.photo_l = this.PhotoData.stbKNK[4]
					this.photo_r = this.PhotoData.stbKNK[5]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
					console.log(this.isNum)
				}
				else if(this.isNum == 7)
				{
					this.popphoto = this.photo04
					this.photo_l = this.PhotoData.stbKNK[8]
					this.photo_r = this.PhotoData.stbKNK[9]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
			}
			else if(isPart == 5)
			{
				if(this.isNum == 0)
				{
					this.popphoto = this.photo05
					this.photo_l = this.PhotoData.stbCSK[1]
					this.photo_r = this.PhotoData.stbCSK[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 3)
				{
					this.popphoto = this.photo05
					this.photo_l = this.PhotoData.stbCSK[4]
					this.photo_r = this.PhotoData.stbCSK[5]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
			}
			else if(isPart == 6)
			{
				if(this.isNum == 0)
				{
					this.popphoto = this.photo06
					this.photo_l = this.PhotoData.stbKOK[1]
					this.photo_r = this.PhotoData.stbKOK[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 3)
				{
					this.popphoto = this.photo06
					this.photo_l = this.PhotoData.stbKOK[4]
					this.photo_r = this.PhotoData.stbKOK[5]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
			}
		},
		isNext(isPart)
		{
			if(isPart == 0)
			{
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check = this.isNum
					this.Location = this.CameraData.Location[1]
					this.photo = this.PhotoData.portWORK[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check = this.isNum
					this.Location = this.CameraData.Location[0]
					this.photo = this.PhotoData.portWORK[this.isNum]
				}
			}
			else if(isPart == 1)
			{
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check01 = this.isNum
					this.Location01 = this.CameraData.Location[3]
					this.photo01 = this.PhotoData.stbGIRL[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check01 = this.isNum
					this.Location01 = this.CameraData.Location[2]
					this.photo01 = this.PhotoData.stbGIRL[this.isNum]
				}
			}
			else if(isPart == 2)
			{
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check02 = this.isNum
					this.Location02 = this.CameraData.Location[5]
					this.photo02 = this.PhotoData.portMEN[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check02 = this.isNum
					this.Location02 = this.CameraData.Location[4]
					this.photo02 = this.PhotoData.portMEN[this.isNum]
				}
			}
			else if(isPart == 3)
			{
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check03 = this.isNum
					this.Location03 = this.CameraData.Location[7]
					this.photo03 = this.PhotoData.stbTOK[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check03 = this.isNum
					this.Location03 = this.CameraData.Location[6]
					this.photo03 = this.PhotoData.stbTOK[this.isNum]
				}
			}
			else if(isPart == 4)
			{
				if(this.isNum == 0)
				{
					this.isNum = 4
					this.check04 = this.isNum
					this.Location04 = this.CameraData.Location[9]
					this.photo04 = this.PhotoData.stbKNK[this.isNum]
				}
				else if(this.isNum == 4)
				{
					this.isNum = 7
					this.check04 = this.isNum
					this.Location04 = this.CameraData.Location[8]
					this.photo04 = this.PhotoData.stbKNK[this.isNum]
				}
				else if(this.isNum == 7)
				{
					this.isNum = 0
					this.check04 = this.isNum
					this.Location04 = this.CameraData.Location[10]
					this.photo04 = this.PhotoData.stbKNK[this.isNum]
				}
			}
			else if(isPart == 5)
			{
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check05 = this.isNum
					this.Location05 = this.CameraData.Location[12]
					this.photo05 = this.PhotoData.stbCSK[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check05 = this.isNum
					this.Location05 = this.CameraData.Location[11]
					this.photo05 = this.PhotoData.stbCSK[this.isNum]
				}
			}
			else if(isPart == 6)
			{
					if(this.isNum == 0)
					{
					this.isNum = 3
					this.check06 = this.isNum
					this.Location06 = this.CameraData.Location[14]
					this.photo06 = this.PhotoData.stbKOK[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check06 = this.isNum
					this.Location06 = this.CameraData.Location[13]
					this.photo06 = this.PhotoData.stbKOK[this.isNum]
				}
			}
		},
		isBack(isPart)
		{
			if(isPart == 0)
			{
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check = this.isNum
					this.Location = this.CameraData.Location[1]
					this.photo = this.PhotoData.portWORK[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check = this.isNum
					this.Location = this.CameraData.Location[0]
					this.photo = this.PhotoData.portWORK[this.isNum]
				}
			}
			else if(isPart == 1)
			{
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check01 = this.isNum
					this.Location01 = this.CameraData.Location[3]
					this.photo01 = this.PhotoData.stbGIRL[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check01 = this.isNum
					this.Location01 = this.CameraData.Location[2]
					this.photo01 = this.PhotoData.stbGIRL[this.isNum]
				}
			}
			else if(isPart == 2)
			{
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check02 = this.isNum
					this.Location02 = this.CameraData.Location[5]
					this.photo02 = this.PhotoData.portMEN[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check02 = this.isNum
					this.Location02 = this.CameraData.Location[4]
					this.photo02 = this.PhotoData.portMEN[this.isNum]
				}
			}
			else if(isPart == 3)
			{
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check03 = this.isNum
					this.Location03 = this.CameraData.Location[7]
					this.photo03 = this.PhotoData.stbTOK[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check03 = this.isNum
					this.Location03 = this.CameraData.Location[6]
					this.photo03 = this.PhotoData.stbTOK[this.isNum]
				}
			}
			else if(isPart == 4)
			{
				if(this.isNum == 0)
				{
					this.isNum = 7
					this.check04 = this.isNum 
					this.Location04 = this.CameraData.Location[8]
					this.photo04 = this.PhotoData.stbKNK[this.isNum]
				}
				else if(this.isNum == 7)
				{
					this.isNum = 3
					this.check04 = this.isNum
					this.Location04 = this.CameraData.Location[9]
					this.photo04 = this.PhotoData.stbKNK[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check04 = this.isNum
					this.Location04 = this.CameraData.Location[10]
					this.photo04 = this.PhotoData.stbKNK[this.isNum]
				}
			}
			else if(isPart == 5)
			{
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check05 = this.isNum
					this.Location05 = this.CameraData.Location[12]
					this.photo05 = this.PhotoData.stbCSK[this.isNum]
				}else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check05 = this.isNum
					this.Location05 = this.CameraData.Location[11]
					this.photo05 = this.PhotoData.stbCSK[this.isNum]
				}
			}
			else if(isPart == 6){
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check06 = this.isNum
					this.Location06 = this.CameraData.Location[14]
					this.photo06 = this.PhotoData.stbKOK[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check06 = this.isNum
					this.Location06 = this.CameraData.Location[13]
					this.photo06 = this.PhotoData.stbKOK[this.isNum]
				}
			}
		},
		cha_l(){
			this.secNum = this.secNum+1
			if(this.secNum == 1){
				this.popphoto_m = this.photo_l
				this.popphoto_l = this.photo_r
				this.popphoto_r = this.popphoto
			}
			else if(this.secNum == 2)
			{
				this.popphoto_m = this.photo_r
				this.popphoto_l = this.popphoto
				this.popphoto_r = this.photo_l
			}
			else if(this.secNum == 3)
			{
				this.popphoto_m = this.popphoto
				this.popphoto_l =this.photo_l
				this.popphoto_r = this.photo_r
				this.secNum = this.secNum-3
			}
		},
		of(){
			this.isShow = false
			this.isNum = 0
			this.popphoto =''
			Object.assign(this.$data, this.$options.data.call(this));
		}
	}
}
</script>

<style lang="scss" scoped>
.ly {
	height: 100%;
}
.bl {
	position: absolute;
	width: 100%;
	top: 10%;
	height: 90%;
	z-index: 1;
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
	width: 100%;
	height: 90vh;
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
	position: absolute;
	width: 95%;
	height: 90%;
	margin: 2.5% 2.5%;
	box-shadow: 5px 5px 0px 0 rgba(26, 28, 29, 0.438)
}
.el_popImg01{
	position: absolute;
	width: 45%;
	height: 40%;
	right: 0;
	transform:rotate(-5deg); 

}
.el_popImg02{
	position: absolute;
	width: 45%;
	height: 40%;
	left: 25%;
	transform:rotate(4deg); 
}
.el_popImg03{
	position: absolute;
	width: 45%;
	height: 40%;
	left: 0%;
	transform:rotate(5deg); 
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
	top: 5%;
	left: 5%;
	width: 90%;
	height: 90%;
	background: rgba(128, 128, 128, 0.925);
	filter: blur(80%);
}
.bl_img_ttl{
	text-align: center;
	position: absolute;
  display: inline-block;
	background: rgba(104, 104, 104, 0.082);
	border-radius: 2%;
	padding: 5px 0;
	border: solid rgba(104, 104, 104, 0.288) 1px;
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
		padding: 3px;
}
.onCircle {
	display: inline-block;
    width: 20px;
    height: 20px; 
    background-color:rgba(0, 0, 128, 0.486);
    border-radius: 50%; 
    text-align: center;/* ←文字を左右に中央揃え */
    line-height: 20px;/* ←文字を上下に中央揃え */
		margin: 5px 10px;
		padding: 3px;
}
</style>