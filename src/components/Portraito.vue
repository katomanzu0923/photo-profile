<template>
	<div class="ly_port">
		<div class="bl_pop" v-if="isUp">
			<button @click="offf()" class="el_pop_btn">✖︎</button>
			<div class="bl_pop_l">
				<img :src="popphoto" class="el_popImg">
			</div>
			<div class="bl_pop_r">
				<div class="bl_pop_r_cont">
					<h2>撮影機種</h2>
					{{Body}}
					<h2>使用レンズ</h2>
					{{Renzu}}
					<h2>状態</h2>
					{{State}}
					<h2>撮影場所</h2>
					{{Location}}
				</div>
			</div>
		</div>
		<div class="bl_btn">
			<p :class="[tabCheck== 0? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(0)">PortRaito</p>
			<p :class="[tabCheck== 1? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(1)">Girl</p>
			<p :class="[tabCheck== 2? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(2)">Boy</p>
		</div>
		<div v-if="tabState==0" >
				<div class="page-l">
					<div class="bl_pht01_l">
						<img class="el_img" :src="photo01">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location}}ー</p><br>
							<button class="el_img_popTxt" type="button" @click="karis(0)">詳細をみる</button>
						</div>
					</div>
				</div>
				<div class="page-r">
					<div class="bl_pht01_r">
						<img class="el_img" :src="photo02">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location02}}ー</p><br>
							<button class="el_img_popTxt" type="button" @click="karis(1)">詳細をみる</button>
						</div>
					</div>
				</div>
			</div>
			<div v-if="tabState==1" >
				<div class="page-l">
					<div class="bl_pht02_l">
						<img class="el_img" :src="photo03">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location03}}ー</p><br>
							<button class="el_img_popTxt" type="button" @click="karis(2)">詳細をみる</button>
						</div>
					</div>
				</div>
				<div class="page-r">
					<div class="bl_pht01_r">
						<img class="el_img" :src="photo04">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location04}}ー</p><br>
							<button class="el_img_popTxt" type="button" @click="karis(3)">詳細をみる</button>
						</div>
					</div>
				</div>
			</div>
			<div v-if="tabState==2" >
				<div class="page-l">
					<div class="bl_pht02_l">
						<img class="el_img" :src="photo05">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location05}}ー</p><br>
							<button class="el_img_popTxt" type="button" @click="karis(4)">詳細をみる</button>
						</div>
					</div>
				</div>
				<div class="page-r">
					<div class="bl_pht01_r">
						<img class="el_img" :src="photo06">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location06}}ー</p><br>
							<button class="el_img_popTxt" type="button" @click="karis(5)">詳細をみる</button>
						</div>
					</div>
				</div>
			</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			isUp:false,
			tabCheck:0,
			tabState:0,
			NumM:'',
			Numl:'',
			Numr:'',
			check:0,
			check01:0,
			check02:0,
			check03:0,
			isPart:0,
			isNum:0,
			isShow:false,
			popphoto:'',
			photo01:require('@/assets/stbHKD01.png'),
			photo02:require('@/assets/stbHSK01.png'),
			photo03:require('@/assets/stbKWG01.png'),
			photo04:require('@/assets/stbUEN01.png'),
			photo05:require('@/assets/stbTYM01.png'),
			photo06:require('@/assets/stbSNPm.png'),
			photo07:require('@/assets/stbHMM01.png'),
			photo08:require('@/assets/stbFOD01.png'),
			photo09:require('@/assets/stbNNZ01.png'),
			photo010:require('@/assets/stbKTN01.png'),
			photo011:require('@/assets/stbIZM01.png'),
			photo012:require('@/assets/stbDGO01.png'),
			photo013:require('@/assets/stbKGM.png'),
			photo014:require('@/assets/stbOKW01.png'),
			photo_l:require('@/assets/stbkobe02.png'),
			photo_r:require('@/assets/stbOKW01.png'),
			popphoto_l:'',
			popphoto_r:'',
			Body:'x-t2',
			Renzu:'10-24',
			State:'F4',
			Location:'函館ベイサイド店',
			Location02:'弘前公園前店',
			Location03:'鐘つき通り店',
			Location04:'上野公園店',
			Location05:'冠水公園店',
			Location06:'スノーピーク白馬村店',
			Location07:'フライトオブドリーム店',
			Location08:'浜松城公園店',
			Location09:'二寧坂店',
			Location010:'北野異人館店',
			Location011:'道後温泉駅店',
			Location012:'出雲大社店',
			Location013:'鹿児島店',
			Location014:'沖縄本町店',
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
				stbHKDTHK: [
					require('@/assets/stbHKD01.png'),
					require('@/assets/stbHSK01.png'),
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
		offf(){
			this.isUp =false
		},
		karis(secNum){
			this.isUp =true
			if(secNum == 0)
			{
				this.popphoto = this.photo01
			}
			else if(secNum == 1)
			{
				this.popphoto = this.photo02
			}
			else if(secNum == 2)
			{
				this.popphoto = this.photo03
			}
			else if(secNum == 3)
			{
				this.popphoto = this.photo04
			}
			else if(secNum == 4)
			{
				this.popphoto = this.photo05
			}
			else if(secNum == 5)
			{
				this.popphoto = this.photo06
			}
			else if(secNum == 6)
			{
				this.popphoto = this.photo07
			}
			else if(secNum == 7)
			{
				this.popphoto = this.photo08
			}
			else if(secNum == 8)
			{
				this.popphoto = this.photo09
			}
			else if(secNum == 9)
			{
				this.popphoto = this.photo010
			}
			else if(secNum == 10)
			{
				this.popphoto = this.photo011
			}
			else if(secNum == 11)
			{
				this.popphoto = this.photo012
			}
			else if(secNum == 12)
			{
				this.popphoto = this.photo013
			}
			else if(secNum == 13)
			{
				this.popphoto = this.photo014   
			}
		},
		changeTab(tab)
		{
			
			if(tab == 0){
				this.tabState = 0
				this.tabCheck = 0
			}
			else if(tab == 1)
			{
				this.tabState = 1
				this.tabCheck = 1
			}
			else if(tab == 2)
			{
				this.tabState = 2
				this.tabCheck = 2
			}
			else if(tab == 3)
			{
				this.tabState =3
				this.tabCheck =3
			}
			else if(tab == 4)
			{
				this.tabState = 4
				this.tabCheck = 4
			}
			else if(tab == 5)
			{
				this.tabState = 5
				this.tabCheck = 5
			}
			else if(tab == 6)
			{
				this.tabState = 6
				this.tabCheck = 6
			}
		},
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
	position: absolute;
	width: 98%;
	left: 1%;
	top: 1%;
	height: 98%;
	background: rgba(236, 235, 235, 0.856);
	border-left: rgb(206, 206, 221) 2px solid;
}
p{
	display: inline-block;
	margin: 2px;
}
button{
	border: none;
	background: none;
}
.bl_btn{
	position: absolute;
	top: 0;
	left: 0;

}

.page-l{
	position: absolute;
	top: 2%;
	z-index: 1;
	width: 50%;
height: 98vh;
}
.page-r{
	position: absolute;
	top: 0%;
	right: 0;
	z-index: 1;
	width: 50%;
	height: 98vh;
	border-left: 1px dotted rgb(110, 76, 25);
}
.el_btn{
	display: inline-block;
}
.bl_pht01_l{
	position: absolute;
	left: 5%;
	top: 15%;
	width: 70%;
	height: 40%;
	z-index: 1;
}
.bl_pht01_r{
	position: absolute;
	left: 15%;
	top: 35%;
	width: 70%;
	height: 40%;
	z-index: 1;
}
.bl_pht02_l{
	position: absolute;
	left: 5%;
	top: 45%;
	width: 70%;
	height: 40%;
	z-index: 1;
}
.el_img{
	position: absolute;
	width: 100%;
	left: 0%;
	height: 90%;
	box-shadow:  0 2px 2px 0 rgba(0, 0, 0, 0.29);
  box-shadow: 2px 2px 2px 0 rgba(0, 0, 0, 0.795);
}
.bl_imgTxt{
	position: absolute;
	top:90%;
	width: 100%;
}
.el_img_posTxt{
	padding: 5px;
	color: rgb(182, 163, 112);
}
.el_img_popTxt{
	padding: 5px;
	color: rgb(179, 169, 169);
}
.el_img_ttl{
  display: inline-block;
	border-radius: 2%;
	border-bottom: blue solid 1px;
	padding: 5px 5px;
	margin: 0;
	border-top: none;
	border-bottom:none;
	box-shadow:  none;
}
.el_img_ttl_def{
  display: inline-block;
	border-radius: 2%;
	padding: 5px 5px;
	margin: 0;
	box-shadow:  0 1px 1px 1px rgba(0, 0, 0, 0.29);

}

.el_img_txt{
	text-align: start;
  display: inline-block;
	padding: 3px;
	margin: 0;
}
.el_img_detail{
	display: inline;
	text-align: right;
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
.defalt{
	text-align: center;
  display: inline-block;
	background: rgba(179, 22, 22, 0.082);
	border-radius: 2%;
	border: solid rgba(104, 104, 104, 0.288) 1px;
	top:0%;
	left: 0%;
}


.el_img_ttl02{
	text-align: center;
  display: inline-block;
	background: rgba(104, 104, 104, 0.082);
	border-radius: 2%;
	border: solid rgba(104, 104, 104, 0.288) 1px;
	top:0%;
	left: 4%;
}

.el_img_ttl03{
	text-align: center;
  display: inline-block;
	background: rgba(104, 104, 104, 0.082);
	border-radius: 2%;
	border: solid rgba(104, 104, 104, 0.288) 1px;
	top:-4%;
	left: 4%;
}

.bl_pop{
	position: absolute;
	height: 90vh;
	width: 90%;
	display: flex;
	justify-content: space-around;
}
.el_popImg{
	margin: 5%;
	width: 90%;
	height: 90%;
}
.el_pop_btn{
	position: absolute;
	left: 0;
	top: 0;
}
.bl_pop_l{
	width: 70%;
}
.bl_pop_r{
	text-align: center;
	width: 30%;
}
.bl_pop_r_cont{
	width: 80%;
	margin-top: 20%;
	text-align: center;
}
</style>