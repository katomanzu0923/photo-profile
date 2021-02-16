<template>
	<div class="ly_port">
		<div class="bl_pop" v-if="isPop">
			<button @click="offf()" class="el_pop_btn">✖︎</button>
			<div class="'bl_pop_l'" >
				<img :src="popmainPhoto" :class="[popState? 'el_popImg': 'el_popImg_ver']">
			</div>
			<div class="bl_pop_r">
				<div class="bl_pop_r_cont">
					<h1 class="el_pop_bodyTtl">撮影機材</h1>
					<p class="el_pop_bodyTtl_cont"><span class="el_pop_bodyTtl_cont_txt">本体:</span>{{Body}}</p><br><p class="el_pop_bodyTtl_cont"><span class="el_pop_bodyTtl_cont_txt">レンズ:</span>{{Renzu}}</p>
					<h1 class="el_pop_stateTtl">撮影状態</h1>
					<p class="el_pop_stateTtl_cont"><span class="el_pop_stateTtl_cont_txt">F値:</span>{{State}}</p>
					<h1 class="el_pop_lcnTtl">撮影場所</h1>
					<p class="el_pop_lcnTtl_cont"><span class="el_pop_stateTtl_cont_txt">場所:</span>{{location}}</p>
					<h2 class="el_pop_pointTtl">ポイント</h2>
					<p class="el_pop_pointTtl_cont">{{Point}}</p>
				</div>
			</div>
		</div>
		<div class="bl_btn">
			<p :class="[tabCheck== 1? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(1)">Girls</p>
			<p :class="[tabCheck== 2? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(2)">Boys</p>
		</div>
		<div v-if="tabState==1" >
				<div v-if="pageNum == 1">
					<div class="bl_pht01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
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
				</div>
				<div v-if="pageNum == 2">
					<div class="bl_pht01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(1,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ーっf{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1,false),emitData(1,2,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,2,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
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
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(2,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht02_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(2,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div v-if="pageNum == 2">
					<div class="bl_pht02_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(2,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ーっf{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht02_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(2,2,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
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
	</div>
</template>

<script>
export default {
	data() {
		return {
			popState:true,
			pageNum:1,
			pageState:1,
			backBtn:false,
			nextBtn:true,
			tabCheck:1,
			tabState:1,
			check:0,
			check01:0,
			check02:0,
			check03:0,
			isPart:0,
			isNum:0,
			isPop:false,
			isShow:false,
			popmainPhoto:'',
			mainPhoto:require('@/assets/portGirl01.png'),
			subPhoto01:require('@/assets/portGirl02.png'),
			subPhoto02:require('@/assets/portGirl03.png'),
			imgTxt_m:false,
			imgTxt_01:false,
			imgTxt_02:false,
			photoState_m:false,
			photoState_01:false,
			photoState_02:false,
			Body:'x-t2',
			Renzu:'10-24',
			State:'F4',
			location:'鮎壺の滝',
			CameraData:{
				Body:['x-t2','x-Pro2'],
				Renzu:['10-24','16-80'],
				State:['F4'],
			},
			LocationData:{
				portLocation:[
					'鮎壺の滝','東京家政大学','江ノ島','東京駅'
				]
			},
			PhotoData:{
				portGirls:[
					require('@/assets/portGirl01.png'),
					require('@/assets/portGirl02.png'),
					require('@/assets/portGirl03.png'),
					require('@/assets/portGirl04.png'),
					require('@/assets/portGirl05.png'),
					require('@/assets/portGirl06.png'),
					require('@/assets/portGirl07.png'),
				],
				portBoys:[
					require('@/assets/portMen02.png'),
					require('@/assets/portMen03.png'),
					require('@/assets/portMen04.png'),
					require('@/assets/portMen05.png'),
				]
			},
			pointData:{
				girlsPoint:[
					'視線と余白を活かして女性の寂しさを主役に。',
					'視線と余白を活かして女性の喜びを主役に。左端から太陽光を入れれば完璧だった',
					'ポージング方向の余白を活かしてモデルの女性を主役に。',
					'対象の女性を並べて主役に。WBの調整不足が露呈',
					'画角、余白のバランスを活かして女性を主役に。'
				],
				boysPoint:[
					'光の入れ具合、視線、上半身の割合を活かして男性を主役に。',
					'視線と上半身の割合、島の切れ目を活かして男性を主役に。右端から太陽光を入れれば完璧だった',
					'東京駅と人のコントラスを活かして人を主役に。',
					'スマートフォンに焦点をあてあえて人を副題に。'
				]
			}
		}
	},
	mounted:{
		ui(){
			this.photo = this.PhotoData.portWORK[0]
		}
	},
	methods:{
		emitData(tabNum,pageNum,photoNum){
			if(tabNum == 1)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.Point = this.pointData.girlsPoint[0]
						console.log(this.pointData.girlsPoint[0])
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.Point = this.pointData.girlsPoint[1]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.Point = this.pointData.girlsPoint[2]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.Point = this.pointData.girlsPoint[3]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.Point = this.pointData.girlsPoint[4]
					}
				}
			}
			else if(tabNum == 2)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.Point = this.pointData.boysPoint[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.Point = this.pointData.boysPoint[1]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.Point = this.pointData.boysPoint[2]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.Point = this.pointData.boysPoint[3]
					}
				}
			}
		},
		isUP(upNum,state)
		{
			this.isPop = true
			if(upNum == 0)
			{
				this.popmainPhoto = this.mainPhoto
				if(state == false){
					this.popState = state
				}
			}
			else if(upNum == 1)
			{
				this.popmainPhoto = this.subPhoto01
				if(state == false){
					this.popState = state
				}
			}
			else if(upNum == 2)
			{
				this.popmainPhoto = this.subPhoto02
				if(state == false){
					this.popState = false
				}
			}
		},
		offf(){
			this.isPop =false
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
					this.mainPhoto = this.PhotoData.portGirls[0]
					this.subPhoto01 = this.PhotoData.portGirls[1]
					this.location = this.LocationData.portLocation[0]
				}
			}else if(tab == 2)
			{
				this.backBtn = true
				this.nextBtn = false
				this.pageNum -=1
				this.mainPhoto = this.PhotoData.portBoys[0]
					this.subPhoto01 = this.PhotoData.portBoys[1]
				this.location = this.LocationData.portLocation[2]
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
					this.mainPhoto = this.PhotoData.portGirls[2]
					this.subPhoto01 = this.PhotoData.portGirls[3]
					this.subPhoto02 = this.PhotoData.portGirls[4]
					this.location = this.LocationData.portLocation[1]
					console.log(this.location)
				}
			}
			else if(tab == 2)
			{
				if(this.pageNum == 1)
				{
					this.backBtn = false
					this.nextBtn = true
					this.pageNum +=1
					this.mainPhoto = this.PhotoData.portBoys[2]
					this.subPhoto01 = this.PhotoData.portBoys[3]
					this.location = this.LocationData.portLocation[3]
				}
			}
		},
		changeTab(tab)
		{
			if(tab == 1){
				this.tabState = 1
				this.tabCheck = 1
				this.pageNum = 1
				this.mainPhoto = this.PhotoData.portGirls[0]
				this.subPhoto01 = this.PhotoData.portGirls[1]
				this.location = this.LocationData.portLocation[0]
			}
			else if(tab == 2)
			{
				this.tabState = 2
				this.tabCheck = 2
				this.pageNum = 1
				this.mainPhoto = this.PhotoData.portBoys[0]
				this.subPhoto01 = this.PhotoData.portBoys[1]
				this.subPhoto02 = this.PhotoData.portBoys[2]
				this.location = this.LocationData.portLocation[2]
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


.bl_pop_ver{
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
	margin: 2.5% 5%;
	width: 90%;
	height: 94%;
}

.el_popImg_ver{
	margin: 5% 25%;
	width: 50%;
	height: 88%;
}

.el_pop_btn{
	position: absolute;
	left: 0;
	top: 0;
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


.bl_pop_ver{
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
	margin: 2.5% 5%;
	width: 90%;
	height: 94%;
}

.el_popImg_ver{
	margin: 5% 25%;
	width: 50%;
	height: 88%;
}

.el_pop_btn{
	position: absolute;
	left: 0;
	top: 0;
}
.bl_pop_l{
}

.bl_pop_ver{
	width: 40%;
}

.bl_pop_r{
	text-align: center;
	height: 80%;
	width: 40%;
	margin: 5% 5%;
	background: rgba(128, 128, 128, 0.521);
}
.bl_pop_r_cont{
	margin-top: 10%;
	text-align: center;
}
.el_pop_bodyTtl_cont{
	width: 80%;
	padding: 1% 1%;
	background: white;
	text-align: start;
	box-shadow:  0 1px 1px 1px rgba(0, 0, 0, 0.29);
}

.el_pop_bodyTtl_cont_txt{
	font-weight:bold;
}

.el_pop_stateTtl_cont{
	width: 80%;
	padding: 1% 1%;
	background: white;
	text-align: start;
	box-shadow:  0 1px 1px 1px rgba(0, 0, 0, 0.29);
}

.el_pop_stateTtl_cont_txt{
	font-weight:bold;
}

.el_pop_lcnTtl_cont{
	width: 80%;
	padding: 1% 1%;
	background: white;
	text-align: start;
	box-shadow:  0 1px 1px 1px rgba(0, 0, 0, 0.29);
}

.el_pop_lcnTtl_cont_txt{
	font-weight:bold;
}

.el_pop_pointTtl_cont{
	width: 80%;
	padding: 1% 1%;
	background: white;
	text-align: start;
	box-shadow:  0 1px 1px 1px rgba(0, 0, 0, 0.29);
}
</style>