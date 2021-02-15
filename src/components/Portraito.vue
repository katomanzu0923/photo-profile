<template>
	<div class="ly_port">
		<div class="bl_pop" v-if="isUp">
			<button @click="offf()" class="el_pop_btn">✖︎</button>
			<div class="bl_pop_l">
				<img :src="popmainPhoto" class="el_popImg">
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
			<p :class="[tabCheck== 1? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(1)">PortRaito</p>
			<p :class="[tabCheck== 2? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(2)">Girl</p>
			<p :class="[tabCheck== 3? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(3)">Boy</p>
		</div>
		<div v-if="tabState==1" >
				<div v-if="pageNum == 1">
					<div class="bl_pht01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div v-if="pageNum == 2">
					<div class="bl_pht01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ーっf{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div class="bl_btnNum">
					<div @click="pageBack(1)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div @click="pageNext(1)" :class="[pageNum !== 2? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
			</div>
			<div v-if="tabState==2" >
				<div v-if="pageNum == 1">
					<div class="bl_pht02_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht02_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht02_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div v-if="pageNum == 2">
					<div class="bl_pht02_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ーっf{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht02_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht02_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div class="bl_btnNum">
					<div @click="pageBack(2)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div @click="pageNext(2)" :class="[pageNum !== 2? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
			</div>
			<div v-if="tabState==3" >
				<div v-if="pageNum == 1">
					<div class="bl_pht03_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht03_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht03_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div v-if="pageNum == 2">
					<div class="bl_pht03_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ーっf{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht03_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht03_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div class="bl_btnNum">
					<div @click="pageBack(3)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div @click="pageNext(3)" :class="[pageNum !== 2? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
			</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			pageNum:1,
			pageState:1,
			backBtn:false,
			nextBtn:true,
			isUp:false,
			tabCheck:1,
			tabState:1,
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
			popmainPhoto:'',
			mainPhoto:require('@/assets/stbHKD01.png'),
			subPhoto01:require('@/assets/stbHKD02.png'),
			subPhoto02:require('@/assets/stbHKD03.png'),
			imgTxt_m:false,
			imgTxt_01:false,
			imgTxt_02:false,
			photoState_m:false,
			photoState_01:false,
			photoState_02:false,
			Body:'x-t2',
			Renzu:'10-24',
			State:'F4',
			Location:'函館ベイサイド店',
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
				stbHKD: [
					require('@/assets/stbHKD01.png'),
					require('@/assets/stbHKD02.png'),
					require('@/assets/stbHKD03.png'),
				],
				stbHSK: [
					require('@/assets/stbHSK01.png'),
					require('@/assets/stbHSK02.png'),
					require('@/assets/stbHSK03.png'),
				],
				stbKWG:[
					require('@/assets/stbKWG01.png'),
					require('@/assets/stbKWG02.png'),
					require('@/assets/stbKWG03.png'),
				],
				stbUEN:[
					require('@/assets/stbUEN01.png'),
					require('@/assets/stbUEN02.png'),
					require('@/assets/stbUEN03.png'),
				],
				stbTYM:[
					require('@/assets/stbTYM01.png'),
					require('@/assets/stbTYM02.png'),
					require('@/assets/stbTYM03.png'),
				],
				stbTYS:[
					require('@/assets/stbSNPm.png'),
					require('@/assets/stbSNP01.png'),
					require('@/assets/stbSNP02.png'),
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
		u(imgNum){
			if(imgNum == 0){
				this.imgTxt_m = true
				this.photoState_m = true
			}
			else if(imgNum == 1)
			{
				this.imgTxt_01 = true
				this.photoState_01 = true
			}
			else if(imgNum == 2)
			{
				this.imgTxt_02 = true
				this.photoState_02 = true
			}
		},
		out(imgNum){
			if(imgNum == 0){
				this.imgTxt_m = false
				this.photoState_m = false
			}
			else if(imgNum == 1)
			{
				this.imgTxt_01 = false
				this.photoState_01 = false
			}
			else if(imgNum == 2)
			{
				this.imgTxt_02 = false
				this.photoState_02 = false
			}
		},
		pageBack(tab){
			if(tab == 1)
			{
				if(this.pageNum == 2)
				{
					this.backBtn = true
					this.nextBtn = false
					this.pageNum -=1
					this.mainPhoto = this.PhotoData.stbHKD[0]
					this.subPhoto01 = this.PhotoData.stbHKD[1]
					this.subPhoto02 = this.PhotoData.stbHKD[2]
					this.location = this.LocationData.stbLocation[0]
				}
			}else if(tab == 2)
			{
				this.backBtn = true
				this.nextBtn = false
				this.pageNum -=1
				this.mainPhoto = this.PhotoData.stbKWG[0]
				this.subPhoto01 = this.PhotoData.stbKWG[1]
				this.subPhoto02 = this.PhotoData.stbKWG[2]
				this.location = this.LocationData.stbLocation[2]
			}
			else if(tab == 3)
			{
				this.backBtn = true
				this.nextBtn = false
				this.pageNum -=1
				this.mainPhoto = this.PhotoData.stbTYM[0]
				this.subPhoto01 = this.PhotoData.stbTYM[1]
				this.subPhoto02 = this.PhotoData.stbTYM[2]
				this.location = this.LocationData.stbLocation[4]
			}
		},
		pageNext(tab){
			if(tab == 1)
			{
				if(this.pageNum == 1)
				{
					this.backBtn = false
					this.nextBtn = true
					this.pageNum +=1
					this.mainPhoto = this.PhotoData.stbHSK[0]
					this.subPhoto01 = this.PhotoData.stbHSK[1]
					this.subPhoto02 = this.PhotoData.stbHSK[2]
					this.location = this.LocationData.stbLocation[1]
				}
			}
			else if(tab == 2)
			{
				if(this.pageNum == 1)
				{
					this.backBtn = false
					this.nextBtn = true
					this.pageNum +=1
					this.mainPhoto = this.PhotoData.stbUEN[0]
					this.subPhoto01 = this.PhotoData.stbUEN[1]
					this.subPhoto02 = this.PhotoData.stbUEN[2]
					this.location = this.LocationData.stbLocation[3]
				}
			}
			else if(tab == 3)
			{
				if(this.pageNum == 1)
				{
					this.backBtn = false
					this.nextBtn = true
					this.pageNum +=1
					this.mainPhoto = this.PhotoData.stbTYS[0]
					this.subPhoto01 = this.PhotoData.stbTYS[1]
					this.subPhoto02 = this.PhotoData.stbTYS[2]
					this.location = this.LocationData.stbLocation[5]
				}
			}
		},
		changeTab(tab)
		{
			if(tab == 1){
				this.tabState = 1
				this.tabCheck = 1
				this.pageNum = 1
				this.mainPhoto = this.PhotoData.stbHKD[0]
				this.subPhoto01 = this.PhotoData.stbHKD[1]
				this.subPhoto02 = this.PhotoData.stbHKD[2]
				this.location = this.LocationData.stbLocation[0]
			}
			else if(tab == 2)
			{
				this.tabState = 2
				this.tabCheck = 2
				this.pageNum = 1
				this.mainPhoto = this.PhotoData.stbKWG[0]
				this.subPhoto01 = this.PhotoData.stbKWG[1]
				this.subPhoto02 = this.PhotoData.stbKWG[2]
				this.location = this.LocationData.stbLocation[2]
			}
			else if(tab == 3)
			{
				this.tabState = 3
				this.tabCheck = 3
				this.pageNum = 1
				this.mainPhoto = this.PhotoData.stbTYM[0]
				this.subPhoto01 = this.PhotoData.stbTYM[1]
				this.subPhoto02 = this.PhotoData.stbTYM[2]
				this.location = this.LocationData.stbLocation[4]
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
.ly_port {
	position: absolute;
	width: 98%;
	left: 1%;
	top: 10%;
	height: 85%;
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



.bl_pht01_m{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 45%;
	z-index: 1;
}
.bl_pht01_sub01{
	position: absolute;
	left: 55%;
	top: 30%;
	width: 30%;
	height: 30%;
	z-index: 1;
}
.bl_pht01_sub02{
	position: absolute;
	left: 60%;
	top: 60%;
	width: 30%;
	height: 30%;
	z-index: 1;
}


.bl_pht02_p01_m{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 15%;
	z-index: 1;
}
.bl_pht02_p01_sub01{
	position: absolute;
	left: 55%;
	top: 30%;
	width: 30%;
	height: 10%;
	z-index: 1;
}
.bl_pht02_p01_sub02{
	position: absolute;
	left: 60%;
	top: 60%;
	width: 30%;
	height: 10%;
	z-index: 1;
}

.bl_pht03_p01_m{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 45%;
	z-index: 1;
}
.bl_pht03_p01_sub01{
	position: absolute;
	left: 55%;
	top: 30%;
	width: 30%;
	height: 30%;
	z-index: 1;
}
.bl_pht03_p01_sub02{
	position: absolute;
	left: 60%;
	top: 60%;
	width: 30%;
	height: 30%;
	z-index: 1;
}

.bl_btnNum{
	position: absolute;
	bottom: 1%;
	width: 100%;
	z-index: 2;
	display: flex;
	justify-content: center;
}
.el_imgNum_txt_js{
	margin: 0 1%;
  text-align: center;
	padding: 3px;
	color: rgba(0, 0, 128, 0.486);
}
.el_imgNum_txt_def{
	margin: 0 1%;
  text-align: center;
	padding: 3px;
	color: rgba(0, 0, 128, 0.137);
}
.onCircle {
  width: 20px;
	margin: 0 1%;
  background-color:rgba(0, 0, 128, 0.712);
  background-color:rgba(0, 0, 128, 0.486);
  border-radius: 50%; 
  text-align: center;
  line-height: 20px;
	padding: 3px;
}
.circle {
  width: 20px;
	margin: 0 1%;
  background-color:rgba(0, 0, 128, 0.712);
  background-color:rgba(0, 0, 128, 0.11);
  border-radius: 50%; 
  text-align: center;
  line-height: 20px;
	padding: 3px;
}
.bl_btn{
	position: absolute;
	top: 0;
	left: 0;
}

.el_pht_txt{
	font-weight: bold;
	position: absolute;
	top       : 45%;
	left      : 50%;
	z-index: -1;
	transform : translate(-50%, -50%);
}

.el_img_hor{
	position: absolute;
	width: 100%;
	left: 0%;
	height: 90%;
	box-shadow:  0 2px 2px 0 rgba(0, 0, 0, 0.29);
  box-shadow: 2px 2px 2px 0 rgba(0, 0, 0, 0.795);
}

.el_img_hor_js{
	position: absolute;
	width: 100%;
	left: 0%;
	height: 90%;
	filter: blur(2px) opacity(30%);
	box-shadow:  0 2px 2px 0 rgba(0, 0, 0, 0.29);
  box-shadow: 2px 2px 2px 0 rgba(0, 0, 0, 0.795);
}
</style>