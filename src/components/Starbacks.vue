<template>
	<div class="ly">
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
				<p :class="[tabCheck== 1? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(1)">北海道・東北</p>
				<p :class="[tabCheck== 2? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(2)">関東</p>
				<p :class="[tabCheck== 3? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(3)">北信越</p>
				<p :class="[tabCheck== 4? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(4)">東海</p>
				<p :class="[tabCheck== 5? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(5)">関西</p>
				<p :class="[tabCheck== 6? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(6)">中国・四国</p>
				<p :class="[tabCheck== 7? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(7)">九州・沖縄</p>
			</div>
			<div v-if="tabState==1" >
				<div class="page-l">
					<div class="bl_pht01_m_l">
						<img class="el_img" :src="mainPhoto_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP(0)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht01_sub01_l">
						<img class="el_img" :src="subPhoto01_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP(1)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht01_sub02_l">
						<img class="el_img" :src="subPhoto02_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP(2)">詳細をみる</button>
						</div>
					</div>
				</div>
				<div class="page-r">
					<div class="bl_pht01_m_r">
						<img class="el_img" :src="mainPhoto_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location02}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP(3)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht01_sub01_r">
						<img class="el_img" :src="subPhoto01_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location02}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP(4)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht01_sub02_r">
						<img class="el_img" :src="subPhoto02_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location02}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP(5)">詳細をみる</button>
						</div>
					</div>
				</div>
			</div>
			<div v-if="tabState==2" >
				<div class="page-l">
					<div class="bl_pht02_m_l">
						<img class="el_img" :src="mainPhoto_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location03}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(2)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht02_sub01_l">
						<img class="el_img" :src="subPhoto01_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location03}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(2)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht02_sub02_l">
						<img class="el_img" :src="subPhoto02_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location03}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(2)">詳細をみる</button>
						</div>
					</div>
				</div>
				<div class="page-r">
					<div class="bl_pht02_m_r">
						<img class="el_img" :src="mainPhoto_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location04}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(3)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht02_sub01_r">
						<img class="el_img" :src="subPhoto01_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location04}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(2)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht02_sub02_r">
						<img class="el_img" :src="subPhoto02_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location04}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(2)">詳細をみる</button>
						</div>
					</div>
				</div>
			</div>
			<div v-if="tabState==3" >
				<div class="page-l">
					<div class="bl_pht03_m_l">
						<img class="el_img" :src="mainPhoto_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location05}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(3)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht03_sub01_l">
						<img class="el_img" :src="subPhoto01_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location05}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(3)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht03_sub02_l">
						<img class="el_img" :src="subPhoto02_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location05}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(3)">詳細をみる</button>
						</div>
					</div>
				</div>
				<div class="page-r">
					<div class="bl_pht03_m_r">
						<img class="el_img" :src="mainPhoto_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location06}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(4)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht03_sub01_r">
						<img class="el_img" :src="subPhoto01_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location06}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(4)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht03_sub02_r">
						<img class="el_img" :src="subPhoto02_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location06}}ー</p><br>
							<button class="el_img_popTxt" @click="karis(4)">詳細をみる</button>
						</div>
					</div>
				</div>
			</div>
			<div v-if="tabState==4" >
				<div class="page-l">
					<div class="bl_pht04_m_l">
						<img class="el_img" :src="mainPhoto_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location07}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(0)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht04_sub01_l">
						<img class="el_img" :src="subPhoto01_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location07}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(1)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht04_sub02_l">
						<img class="el_img" :src="subPhoto02_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(2)">詳細をみる</button>
						</div>
					</div>
				</div>
				<div class="page-r">
					<div class="bl_pht04_m_r">
						<img class="el_img" :src="mainPhoto_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(3)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht04_sub01_r">
						<img class="el_img" :src="subPhoto01_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(4)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht04_sub02_r">
						<img class="el_img" :src="subPhoto02_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(5)">詳細をみる</button>
						</div>
					</div>
				</div>
			</div>
			<div v-if="tabState==5" >
				<div class="page-l">
					<div class="bl_pht05_m_l">
						<img class="el_img" :src="mainPhoto_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location07}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(0)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht05_sub01_l">
						<img class="el_img" :src="subPhoto01_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location07}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(1)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht05_sub02_l">
						<img class="el_img" :src="subPhoto02_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(2)">詳細をみる</button>
						</div>
					</div>
				</div>
				<div class="page-r">
					<div class="bl_pht05_m_r">
						<img class="el_img" :src="mainPhoto_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(3)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht05_sub01_r">
						<img class="el_img" :src="subPhoto01_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(4)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht05_sub02_r">
						<img class="el_img" :src="subPhoto02_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(5)">詳細をみる</button>
						</div>
					</div>
				</div>
			</div>
			<div v-if="tabState==6" >
				<div class="page-l">
					<div class="bl_pht06_m_l">
						<img class="el_img" :src="mainPhoto_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location07}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(0)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht06_sub01_l">
						<img class="el_img" :src="subPhoto01_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location07}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(1)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht06_sub02_l">
						<img class="el_img" :src="subPhoto02_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(2)">詳細をみる</button>
						</div>
					</div>
				</div>
				<div class="page-r">
					<div class="bl_pht06_m_r">
						<img class="el_img" :src="mainPhoto_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(3)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht06_sub01_r">
						<img class="el_img" :src="subPhoto01_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(4)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht06_sub02_r">
						<img class="el_img" :src="subPhoto02_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(5)">詳細をみる</button>
						</div>
					</div>
				</div>
			</div>
			<div v-if="tabState==7" >
				<div class="page-l">
					<div class="bl_pht07_m_l">
						<img class="el_img" :src="mainPhoto_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location07}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(0)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht07_sub01_l">
						<img class="el_img" :src="subPhoto01_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location07}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(1)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht07_sub02_l">
						<img class="el_img" :src="subPhoto02_l">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(2)">詳細をみる</button>
						</div>
					</div>
				</div>
				<div class="page-r">
					<div class="bl_pht07_m_r">
						<img class="el_img" :src="mainPhoto_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(3)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht07_sub01_r">
						<img class="el_img" :src="subPhoto01_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(4)">詳細をみる</button>
						</div>
					</div>
					<div class="bl_pht07_sub02_r">
						<img class="el_img" :src="subPhoto02_r">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{Location08}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP_TOK(5)">詳細をみる</button>
						</div>
					</div>
				</div>
			</div>
			<!--  
			<div class="bl_img">
				<span class="el_img_ttl">Boy</span>
				<img class="el_popImg" :src="mainPhoto02"><p class="el_img_ttl">{{Location02}}</p>
				<div class="bl_circle">
					<div :class="[check02 === 0? 'onCircle': 'circle']">1</div>
				</div>
				<div class="bl_imgBtn">
					<p class="el_btn" @click="isBack(2)">Back</p><p class="el_Btn" type="p" @click="chi(2)">詳細へ</p><p @click="isNext(2)" class="el_btn">Next</p>
				</div>
			</div> 
		-->
	</div>
</template>

<script>
export default {
	data() {
		return {
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
			mainPhoto_l:require('@/assets/stbHKD01.png'),
			subPhoto01_l:require('@/assets/stbHKD02.png'),
			subPhoto02_l:require('@/assets/stbHKD03.png'),
			mainPhoto_r:require('@/assets/stbHSK01.png'),
			subPhoto01_r:require('@/assets/stbHSK02.png'),
			subPhoto02_r:require('@/assets/stbHSK03.png'),
			popmainPhoto_l:'',
			popmainPhoto_r:'',
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
					require('@/assets/stbTYM01.png'),
					require('@/assets/stbTYM02.png'),
					require('@/assets/stbTYM03.png'),
				],
				stbFOD:[
					require('@/assets/stbFOD01.png'),
					require('@/assets/stbFOD02.png'),
					require('@/assets/stbFOD03.png'),
				],
				stbHMM:[
					require('@/assets/stbHMM01.png'),
					require('@/assets/stbHMM02.png'),
					require('@/assets/stbHMM03.png'),
				],
				stbNNZ:[
					require('@/assets/stbNNZ01.png'),
					require('@/assets/stbNNZ02.png'),
					require('@/assets/stbNNZ03.png'),
				],
				stbKTN:[
					require('@/assets/stbKTN01.png'),
					require('@/assets/stbKTN02.png'),
					require('@/assets/stbKTN03.png'),
				],
				stbIZM:[
					require('@/assets/stbIZM01.png'),
					require('@/assets/stbIZM02.png'),
					require('@/assets/stbIZM03.png'),
				],
				stbDGO:[
					require('@/assets/stbDGO01.png'),
					require('@/assets/stbDGO02.png'),
					require('@/assets/stbDGO03.png'),
				],
				stbKGM:[
					require('@/assets/stbKGM.png'),
					require('@/assets/stbKGM02.png'),
					require('@/assets/stbKGM03.png'),
				],
				stbOKW:[
					require('@/assets/stbOKW01.png'),
					require('@/assets/stbOKW02.png'),
					require('@/assets/stbOKW03.png'),
				]
			},
		}
	},
	mounted:{
		ui(){
			this.mainPhoto = this.mainPhotoData.stbHKD[0]
		}
	},
	methods:{
		offf(){
			this.isUp =false
		},
		isUP(upNum)
		{
			this.isUp = true
			if(this.tabState == 1)
			{
				if(upNum == 0)
				{
					this.popmainPhoto = this.mainPhoto_l
				}
				else if(upNum == 1)
				{
					this.popmainPhoto = this.subPhoto01_l
				}
				else if(upNum == 2)
				{
					this.popmainPhoto = this.subPhoto02_l
				}
				else if(upNum == 3)
				{
					this.popmainPhoto = this.mainPhoto_r
				}
				else if(upNum == 4)
				{
					this.popmainPhoto = this.subPhoto01_r
				}
				else if(upNum == 5)
				{
					this.popmainPhoto = this.subPhoto02_r
				}
			}
		},
		changeTab(tab)
		{
			if(tab == 1){
				this.tabState = 1
				this.tabCheck = 1
				this.mainPhoto_l = this.PhotoData.stbHKD[0]
				this.subPhoto01_l = this.PhotoData.stbHKD[1]
				this.subPhoto02_l = this.PhotoData.stbHKD[2]
				this.mainPhoto_r = this.PhotoData.stbHSK[0]
				this.subPhoto01_r = this.PhotoData.stbHSK[1]
				this.subPhoto02_r = this.PhotoData.stbHSK[2]
			}
			else if(tab == 2)
			{
				this.tabState = 2
				this.tabCheck = 2
				this.mainPhoto_l = this.PhotoData.stbKWG[0]
				this.subPhoto01_l = this.PhotoData.stbKWG[1]
				this.subPhoto02_l = this.PhotoData.stbKWG[2]
				this.mainPhoto_r = this.PhotoData.stbUEN[0]
				this.subPhoto01_r = this.PhotoData.stbUEN[1]
				this.subPhoto02_r = this.PhotoData.stbUEN[2]
			}
			else if(tab == 3)
			{
				this.tabState = 3
				this.tabCheck = 3
				this.mainPhoto_l = this.PhotoData.stbTYM[0]
				this.subPhoto01_l = this.PhotoData.stbTYM[1]
				this.subPhoto02_l = this.PhotoData.stbTYM[2]
				this.mainPhoto_r = this.PhotoData.stbUEN[0]
				this.subPhoto01_r = this.PhotoData.stbUEN[1]
				this.subPhoto02_r = this.PhotoData.stbUEN[2]
			}
			else if(tab == 4)
			{
				this.tabState =4
				this.tabCheck =4
				this.mainPhoto_l = this.PhotoData.stbFOD[0]
				this.subPhoto01_l = this.PhotoData.stbFOD[1]
				this.subPhoto02_l = this.PhotoData.stbFOD[2]
				this.mainPhoto_r = this.PhotoData.stbHMM[0]
				this.subPhoto01_r = this.PhotoData.stbHMM[1]
				this.subPhoto02_r = this.PhotoData.stbHMM[2]
			}
			else if(tab == 5)
			{
				this.tabState =5
				this.tabCheck =5
				this.mainPhoto_l = this.PhotoData.stbNNZ[0]
				this.subPhoto01_l = this.PhotoData.stbNNZ[1]
				this.subPhoto02_l = this.PhotoData.stbNNZ[2]
				this.mainPhoto_r = this.PhotoData.stbKTN[0]
				this.subPhoto01_r = this.PhotoData.stbKTN[1]
				this.subPhoto02_r = this.PhotoData.stbKTN[2]
			}
			else if(tab == 6)
			{
				this.tabState = 6
				this.tabCheck = 6
				this.mainPhoto_l = this.PhotoData.stbIZM[0]
				this.subPhoto01_l = this.PhotoData.stbIZM[1]
				this.subPhoto02_l = this.PhotoData.stbIZM[2]
				this.mainPhoto_r = this.PhotoData.stbDGO[0]
				this.subPhoto01_r = this.PhotoData.stbDGO[1]
				this.subPhoto02_r = this.PhotoData.stbDGO[2]
			}
			else if(tab == 7)
			{
				this.tabState = 7
				this.tabCheck = 7
				this.mainPhoto_l = this.PhotoData.stbKGM[0]
				this.subPhoto01_l = this.PhotoData.stbKGN[1]
				this.subPhoto02_l = this.PhotoData.stbKGM[2]
				this.mainPhoto_r = this.PhotoData.stbOKW[0]
				this.subPhoto01_r = this.PhotoData.stbOKW[1]
				this.subPhoto02_r = this.PhotoData.stbOKW[2]
			}
		},
		of(){
			this.isShow = false
			this.isNum = 0
			this.popmainPhoto =''
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
	outline: none;
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
.bl_pht01_m_l{
	position: absolute;
	left: 10%;
	top: 5%;
	width: 80%;
	height: 45%;
	z-index: 1;
}
.bl_pht01_sub01_l{
	position: absolute;
	left: 55%;
	top: 50%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht01_sub02_l{
	position: absolute;
	left: 10%;
	top: 60%;
	width: 40%;
	height: 30%;
	z-index: 1;
}
.bl_pht01_m_r{
	position: absolute;
	left: 15%;
	top: 55%;
	width: 50%;
	height: 40%;
	z-index: 1;
}
.bl_pht01_sub01_r{
	position: absolute;
	left: 55%;
	top: 10%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht01_sub02_r{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 30%;
	z-index: 1;
}
.bl_pht02_m_l{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 70%;
	height: 40%;
	z-index: 1;
}
.bl_pht02_sub01_l{
	position: absolute;
	left: 55%;
	top: 50%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht02_sub02_l{
	position: absolute;
	left: 15%;
	top: 50%;
	width: 35%;
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
	height: 100%;
	left: 0;
	top: 0;
	width: 100%;
	display: flex;
	background: rgba(233, 231, 231, 0.856);
	filter: blur(30%);
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