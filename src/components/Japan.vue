<template>
	<div class="ly">
		<div class="bl01">
			<div v-show="isShow" class="bl_pop">
				<div>
					<button @click="of()">✖︎</button>{{height}}
				</div>
				<div class="imge">
					<img class="imgf" :src="popphoto_m">
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
						<button @click="cha_l()">他の写真をみる</button>
						<p><img class="el_popImg_l" :src="popphoto_l" type="button" @click="cha_l()"></p>
						<p><img class="el_popImg_r" :src="popphoto_r" type="button" @click="cha_r()"></p>
					</div>
				</div>
			</div>
		</div>
		<div class="bl">
			<div class="bl_img">
				<span class="bl_img_ttl">北海道・東北</span>
				<img class="el_popImg" :src="photo"><p class="el_img_ttl">{{Location}}</p>
				<div class="bl_circle">
					<div :class="[check === 0? 'onCircle': 'circle']">1</div>
					<div :class="[check === 1? 'onCircle': 'circle']">2</div>
					<div :class="[check === 2? 'onCircle': 'circle']">3</div>
					<div :class="[check === 3? 'onCircle': 'circle']">4</div>
					<div :class="[check === 4? 'onCircle': 'circle']">5</div>
				</div>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(0)">Back</button><button class="el_Btn" type="button" @click="chi(0)">詳細へ</button><button @click="isNext(0)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">関東</span>
				<img class="el_popImg" :src="photo01" ><p class="el_img_ttl">{{Location01}}</p>
				<div class="bl_circle">
					<div :class="[check01 === 0? 'onCircle': 'circle']">1</div>
					<div :class="[check01 === 1? 'onCircle': 'circle']">2</div>
					<div :class="[check01 === 2? 'onCircle': 'circle']">3</div>
					<div :class="[check01 === 3? 'onCircle': 'circle']">4</div>
				</div>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(1)">Back</button><button class="el_Btn" type="button" @click="chi(1)">詳細へ</button><button @click="isNext(1)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">北信越</span>
				<img class="el_popImg" :src="photo02"><p class="el_img_ttl">{{Location02}}</p>
				<div class="bl_circle">
					<div :class="[check02 === 0? 'onCircle': 'circle']">1</div>
					<div :class="[check02 === 1? 'onCircle': 'circle']">2</div>
					<div :class="[check02 === 2? 'onCircle': 'circle']">3</div>
				</div>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(2)">Back</button><button class="el_Btn" type="button" @click="chi(2)">詳細へ</button><button @click="isNext(2)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">東海</span>
				<img class="el_popImg" :src="photo03"><p class="el_img_ttl">{{Location03}}</p>
				<div class="bl_circle">
					<div :class="[check03 === 0? 'onCircle': 'circle']">1</div>
					<div :class="[check03 === 1? 'onCircle': 'circle']">2</div>
				</div>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(3)">Back</button><button class="el_Btn" type="button" @click="chi(3)">詳細へ</button><button @click="isNext(3)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">関西</span>
				<img class="el_popImg" :src="photo04"><p class="el_img_ttl">{{Location04}}</p>
				<div class="bl_circle">
					<div :class="[check04 === 0? 'onCircle': 'circle']">1</div>
					<div :class="[check04 === 1? 'onCircle': 'circle']">2</div>
				</div>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(4)">Back</button><button class="el_Btn" type="button" @click="chi(4)">詳細へ</button><button @click="isNext(4)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">中国・四国</span>
				<img class="el_popImg" :src="photo05"><p class="el_img_ttl">{{Location05}}</p>
				<div class="bl_circle">
					<div :class="[check05 === 0? 'onCircle': 'circle']">1</div>
					<div :class="[check05 === 1? 'onCircle': 'circle']">2</div>
				</div>
				<div class="bl_imgBtn">
					<button class="el_btn" @click="isBack(5)">Back</button><button class="el_Btn" type="button" @click="chi(5)">詳細へ</button><button @click="isNext(5)" class="el_btn">Next</button>
				</div>
			</div>
			<div class="bl_img">
				<span class="bl_img_ttl">九州・沖縄</span>
				<img class="el_popImg" :src="photo06"><p class="el_img_ttl">{{Location06}}</p>
				<div class="bl_circle">
					<div :class="[check06 === 0? 'onCircle': 'circle']">1</div>
					<div :class="[check06 === 1? 'onCircle': 'circle']">2</div>
					<div :class="[check06 === 2? 'onCircle': 'circle']">3</div>
				</div>
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
			height:0,
			NumM:'',
			Numl:'',
			Numr:'',
			secNum:0,
			check:0,
			check01:0,
			check02:0,
			check03:0,
			check04:0,
			check05:0,
			check06:0,
			isPart:0,
			isNum:0,
			isShow:false,
			popphoto:'',
			photo:require('@/assets/japanHKD01.png'),
			photo01:require('@/assets/japanSHN01.png'),
			photo02:require('@/assets/japanNGNm.png'),
			photo03:require('@/assets/japanMIEm.png'),
			photo04:require('@/assets/japanKYOm.png'),
			photo05:require('@/assets/japanHRSm.png'),
			photo06:require('@/assets/stbOKW01.png'),
			photo_l:require('@/assets/stbkobe02.png'),
			photo_r:require('@/assets/stbOKW01.png'),
			popphoto_l:'',
			popphoto_r:'',
			Body:'x-t2',
			Renzu:'10-24',
			State:'F4',
			Location:'函館山',
			Location01:'江ノ島',
			Location02:'妻籠宿',
			Location03:'伊勢神宮',
			Location04:'三寧坂',
			Location05:'原爆ドーム',
			Location06:'桜島',
			CameraData:{
				Body:['x-t2','x-Pro2'],
				Renzu:['10-24','16-80'],
				State:['F4'],
			},
			LocationData:{
				LocationHKDTHK:['函館山','美瑛町','乳頭温泉郷','弘前城','清津峡'],
				LocationKNT:['江ノ島','江川海岸','日立駅','東京駅'],
				LocationHSE:['妻籠宿','河口湖','東尋坊'],
				LocationTOK:['伊勢神宮','白川郷'],
				LocationKNK:['三寧坂','白髭神社',],
				LocationCSK:['原爆ドーム記念公園','高屋神社'],
				LocationKOK:['桜島','稲佐山','美ら海水族館']
			},
			PhotoData:{
				japanHKDTHK: [
					require('@/assets/japanHKD01.png'),
					require('@/assets/japanBEI01.png'),
					require('@/assets/japanAKT01.png'),
					require('@/assets/japanHSK01.png'),
					require('@/assets/japanNGT02.png'),
				],
				japanKNT: [
					require('@/assets/japanSHN01.png'),
					require('@/assets/japanTIB01.png'),
					require('@/assets/japanIBG01.png'),
					require('@/assets/japanTKOm.png'),
				],
				japanHSE: [
					require('@/assets/japanNGNm.png'),
					require('@/assets/japanYMNm.png'),
					require('@/assets/japanFKIm.png'),
				],
				japanTOK: [
					require('@/assets/japanMIEm.png'),
					require('@/assets/japanGIFm.png'),
					require('@/assets/japanMIE01.png'),
					require('@/assets/japanMIE02.png'),
					require('@/assets/japanGIF01.png'),
					require('@/assets/stbHMM03.png')
				],
				japanKNK: [
					require('@/assets/japanKYOm.png'),
					require('@/assets/japanSIGm.png'),
					require('@/assets/japanKOB02.png'),
					require('@/assets/japanMIE02.png'),
					require('@/assets/japanGIF01.png'),
					require('@/assets/stbHMM03.png')
				],
				japanCSK: [
					require('@/assets/japanHRSm.png'),
					require('@/assets/japanKGWm.png'),
					require('@/assets/japanKGW01.png'),
					require('@/assets/japanKGW02.png'),
					require('@/assets/japanHRS02.png'),
					require('@/assets/japanMIE01.png'),
					require('@/assets/japanMIE02.png'),
					require('@/assets/japanGIF01.png'),
				],
				japanKOK: [
					require('@/assets/japanKGSm.png'),
					require('@/assets/japanNGSm.png'),
					require('@/assets/japanOKWm.png'),
					require('@/assets/japanKGW02.png'),
					require('@/assets/japanHRS02.png'),
					require('@/assets/japanMIE01.png'),
					require('@/assets/japanMIE02.png'),
					require('@/assets/japanGIF01.png'),
				],
			},
		}
	},
	mounted:{
		ui(){
			this.photo = this.PhotoData.japanHKDTHK[0]
		}
  },
	methods:{
		chi(isPart)
		{
			this.isShow = true
			const posi = window.pageYOffset
			let height = posi
			this.height = height
			window.scrollTo({
				top: top
			});
			if(isPart == 0)
			{
				if(this.isNum == 0)
				{
					this.popphoto = this.photo
					this.Body = this.CameraData.Body[0]
					this.Renzu = this.CameraData.Renzu[1]
					this.State = this.CameraData.State[0]
					this.photo_l = this.PhotoData.japanHKDTHK[1]
					this.photo_r = this.PhotoData.japanHKDTHK[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 1)
				{
					this.popphoto = this.photo
					this.Body = this.CameraData.Body[1]
					this.Renzu = this.CameraData.Renzu[1]
					this.State = this.CameraData.State[0]
					this.photo_l = this.PhotoData.japanHKDTHK[4]
					this.photo_r = this.PhotoData.japanHKDTHK[5]
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
					this.photo_l = this.PhotoData.japanKNT[1]
					this.photo_r = this.PhotoData.japanKNT[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 3)
				{
					this.popphoto = this.photo01
					this.photo_l = this.PhotoData.japanKNT[4]
					this.photo_r = this.PhotoData.japanKNT[5]
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
					this.photo_l = this.PhotoData.japanHSE[1]
					this.photo_r = this.PhotoData.japanHSE[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 3)
				{
					this.popphoto = this.photo02
					this.photo_l = this.PhotoData.japanHSE[4]
					this.photo_r = this.PhotoData.japanHSE[5]
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
					this.photo_l = this.PhotoData.japanTOK[1]
					this.photo_r = this.PhotoData.japanTOK[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 3)
				{
					this.popphoto = this.photo03
					this.photo_l = this.PhotoData.japanTOK[4]
					this.photo_r = this.PhotoData.japanTOK[5]
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
					this.photo_l = this.PhotoData.japanKNK[1]
					this.photo_r = this.PhotoData.japanKNK[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 4)
				{
					this.popphoto = this.photo04
					this.photo_l = this.PhotoData.japanKNK[4]
					this.photo_r = this.PhotoData.japanKNK[5]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
					console.log(this.isNum)
				}
				else if(this.isNum == 7)
				{
					this.popphoto = this.photo04
					this.photo_l = this.PhotoData.japanKNK[8]
					this.photo_r = this.PhotoData.japanKNK[9]
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
					this.photo_l = this.PhotoData.japanCSK[1]
					this.photo_r = this.PhotoData.japanCSK[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 1)
				{
					this.popphoto = this.photo05
					this.photo_l = this.PhotoData.japanCSK[4]
					this.photo_r = this.PhotoData.japanCSK[5]
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
					this.photo_l = this.PhotoData.japanKOK[1]
					this.photo_r = this.PhotoData.japanKOK[2]
					this.popphoto_m = this.popphoto
					this.popphoto_l = this.photo_l
					this.popphoto_r = this.photo_r
				}
				else if(this.isNum == 3)
				{
					this.popphoto = this.photo06
					this.photo_l = this.PhotoData.japanKOK[4]
					this.photo_r = this.PhotoData.japanKOK[5]
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
					this.isNum = 1
					this.check = this.isNum
					this.Location = this.LocationData.LocationHKDTHK[1]
					this.photo = this.PhotoData.japanHKDTHK[this.isNum]
				}
				else if(this.isNum == 1)
				{
					this.isNum = 2
					this.check = this.isNum
					this.Location = this.LocationData.LocationHKDTHK[2]
					this.photo = this.PhotoData.japanHKDTHK[this.isNum]
				}
				else if(this.isNum == 2)
				{
					this.isNum = 3
					this.check = this.isNum
					this.Location = this.LocationData.LocationHKDTHK[3]
					this.photo = this.PhotoData.japanHKDTHK[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 4
					this.check = this.isNum
					this.Location = this.LocationData.LocationHKDTHK[4]
					this.photo = this.PhotoData.japanHKDTHK[this.isNum]
				}
				else if(this.isNum == 4)
				{
					this.isNum = 0
					this.check = this.isNum
					this.Location = this.LocationData.LocationHKDTHK[0]
					this.photo = this.PhotoData.japanHKDTHK[this.isNum]
				}
			}
			else if(isPart == 1)
			{
				if(this.isNum == 0)
				{
					this.isNum = 1
					this.check01 = this.isNum
					this.Location01 = this.LocationData.LocationKNT[1]
					this.photo01 = this.PhotoData.japanKNT[this.isNum]
				}
				else if(this.isNum == 1)
				{
					this.isNum = 2
					this.check01 = this.isNum
					this.Location01 = this.LocationData.LocationKNT[2]
					this.photo01 = this.PhotoData.japanKNT[this.isNum]
				}
				else if(this.isNum == 2)
				{
					this.isNum = 3
					this.check01 = this.isNum
					this.Location01 = this.LocationData.LocationKNT[3]
					this.photo01 = this.PhotoData.japanKNT[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check01 = this.isNum
					this.Location01 = this.LocationData.LocationKNT[0]
					this.photo01 = this.PhotoData.japanKNT[this.isNum]
				}
			}
			else if(isPart == 2)
			{
				if(this.isNum == 0)
				{
					this.isNum = 1
					this.check02 = this.isNum
					this.Location02 = this.LocationData.LocationHSE[1]
					this.photo02 = this.PhotoData.japanHSE[this.isNum]
				}
				else if(this.isNum == 1)
				{
					this.isNum = 2
					this.check02 = this.isNum
					this.Location02 = this.LocationData.LocationHSE[2]
					this.photo02 = this.PhotoData.japanHSE[this.isNum]
				}
				else if(this.isNum == 2)
				{
					this.isNum = 0
					this.check02 = this.isNum
					this.Location02 = this.LocationData.LocationHSE[0]
					this.photo02 = this.PhotoData.japanHSE[this.isNum]
				}
			}
			else if(isPart == 3)
			{
				if(this.isNum == 0)
				{
					this.isNum = 1
					this.check03 = this.isNum
					this.Location03 = this.LocationData.LocationTOK[1]
					this.photo03 = this.PhotoData.japanTOK[this.isNum]
				}
				else if(this.isNum == 1)
				{
					this.isNum = 0
					this.check03 = this.isNum
					this.Location03 = this.LocationData.LocationTOK[0]
					this.photo03 = this.PhotoData.japanTOK[this.isNum]
				}
			}
			else if(isPart == 4)
			{
				if(this.isNum == 0)
				{
					this.isNum = 1
					this.check04 = this.isNum
					this.Location04 = this.LocationData.LocationKNK[1]
					this.photo04 = this.PhotoData.japanKNK[this.isNum]
				}
				else if(this.isNum == 1)
				{
					this.isNum = 0
					this.check04 = this.isNum
					this.Location04 = this.LocationData.LocationKNK[0]
					this.photo04 = this.PhotoData.japanKNK[this.isNum]
				}
			}
			else if(isPart == 5)
			{
				if(this.isNum == 0)
				{
					this.isNum = 1
					this.check05 = this.isNum
					this.Location05 = this.LocationData.LocationCSK[1]
					this.photo05 = this.PhotoData.japanCSK[this.isNum]
				}
				else if(this.isNum == 1)
				{
					this.isNum = 0
					this.check05 = this.isNum
					this.Location05 = this.LocationData.LocationCSK[0]
					this.photo05 = this.PhotoData.japanCSK[this.isNum]
				}
			}
			else if(isPart == 6)
			{
					if(this.isNum == 0)
					{
					this.isNum = 1
					this.check06 = this.isNum
					this.Location06 = this.LocationData.LocationKOK[1]
					this.photo06 = this.PhotoData.japanKOK[this.isNum]
				}
				else if(this.isNum == 1)
				{
					this.isNum = 2
					this.check06 = this.isNum
					this.Location06 = this.LocationData.LocationKOK[2]
					this.photo06 = this.PhotoData.japanKOK[this.isNum]
				}
				else if(this.isNum == 2)
				{
					this.isNum = 0
					this.check06 = this.isNum
					this.Location06 = this.LocationData.LocationKOK[0]
					this.photo06 = this.PhotoData.japanKOK[this.isNum]
				}
			}
		},
		isBack(isPart)
		{
			if(isPart == 0)
			{
				if(this.isNum == 0)
				{
					this.isNum = 4
					this.check = this.isNum
					this.Location = this.CameraData.Location[1]
					this.photo = this.PhotoData.japanHKDTHK[this.isNum]
				}
				else if(this.isNum == 4)
				{
					this.isNum = 3
					this.check = this.isNum
					this.Location = this.CameraData.Location[1]
					this.photo = this.PhotoData.japanHKDTHK[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 2
					this.check = this.isNum
					this.Location = this.CameraData.Location[1]
					this.photo = this.PhotoData.japanHKDTHK[this.isNum]
				}
				else if(this.isNum == 2)
				{
					this.isNum = 1
					this.check = this.isNum
					this.Location = this.CameraData.Location[1]
					this.photo = this.PhotoData.japanHKDTHK[this.isNum]
				}
				else if(this.isNum == 1)
				{
					this.isNum = 0
					this.check = this.isNum
					this.Location = this.CameraData.Location[1]
					this.photo = this.PhotoData.japanHKDTHK[this.isNum]
				}
			}
			else if(isPart == 1)
			{
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check01 = this.isNum
					this.Location01 = this.CameraData.Location[3]
					this.photo01 = this.PhotoData.japanKNT[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check01 = this.isNum
					this.Location01 = this.CameraData.Location[2]
					this.photo01 = this.PhotoData.japanKNT[this.isNum]
				}
			}
			else if(isPart == 2)
			{
				if(this.isNum == 0)
				{
					this.isNum = 2
					this.check02 = this.isNum
					this.Location02 = this.CameraData.Location[5]
					this.photo02 = this.PhotoData.japanHSE[this.isNum]
				}
				else if(this.isNum == 2)
				{
					this.isNum = 1
					this.check02 = this.isNum
					this.Location02 = this.CameraData.Location[4]
					this.photo02 = this.PhotoData.japanHSE[this.isNum]
				}
				else if(this.isNum == 1)
				{
					this.isNum = 0
					this.check02 = this.isNum
					this.Location02 = this.CameraData.Location[4]
					this.photo02 = this.PhotoData.japanHSE[this.isNum]
				}
			}
			else if(isPart == 3)
			{
				if(this.isNum == 0)
				{
					this.isNum = 1
					this.check03 = this.isNum
					this.Location03 = this.CameraData.Location[7]
					this.photo03 = this.PhotoData.japanTOK[this.isNum]
				}
				else if(this.isNum == 1)
				{
					this.isNum = 0
					this.check03 = this.isNum
					this.Location03 = this.CameraData.Location[6]
					this.photo03 = this.PhotoData.japanTOK[this.isNum]
				}
			}
			else if(isPart == 4)
			{
				if(this.isNum == 0)
				{
					this.isNum = 1
					this.check04 = this.isNum 
					this.Location04 = this.CameraData.Location[8]
					this.photo04 = this.PhotoData.japanKNK[this.isNum]
				}
				else if(this.isNum == 1)
				{
					this.isNum = 0
					this.check04 = this.isNum
					this.Location04 = this.CameraData.Location[9]
					this.photo04 = this.PhotoData.japanKNK[this.isNum]
				}
			}
			else if(isPart == 5)
			{
				if(this.isNum == 0)
				{
					this.isNum = 1
					this.check05 = this.isNum
					this.Location05 = this.CameraData.Location[12]
					this.photo05 = this.PhotoData.japanCSK[this.isNum]
				}else if(this.isNum == 1)
				{
					this.isNum = 0
					this.check05 = this.isNum
					this.Location05 = this.CameraData.Location[11]
					this.photo05 = this.PhotoData.japanCSK[this.isNum]
				}
			}
			else if(isPart == 6){
				if(this.isNum == 0)
				{
					this.isNum = 3
					this.check06 = this.isNum
					this.Location06 = this.CameraData.Location[14]
					this.photo06 = this.PhotoData.japanKOK[this.isNum]
				}
				else if(this.isNum == 3)
				{
					this.isNum = 0
					this.check06 = this.isNum
					this.Location06 = this.CameraData.Location[13]
					this.photo06 = this.PhotoData.japanKOK[this.isNum]
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
			let popPosi = this.height
			Object.assign(this.$data, this.$options.data.call(this));
			window.scrollBy(0,popPosi);
			console.log(popPosi)
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
	border: solid rgba(104, 104, 104, 0.288) 1px;
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