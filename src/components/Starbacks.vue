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
			<div v-if="tabState==4" >
				<div v-if="pageNum == 1">
					<div class="bl_pht04_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht04_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht04_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div v-if="pageNum == 2">
					<div class="bl_pht04_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ーっf{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht04_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht04_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div class="bl_btnNum">
					<div @click="pageBack(4)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div @click="pageNext(4)" :class="[pageNum !== 2? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
				</div>
			</div>
			<div v-if="tabState==5" >
				<div v-if="pageNum == 1">
					<div class="bl_pht05_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht05_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht05_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div v-if="pageNum == 2">
					<div class="bl_pht05_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ーっf{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht05_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht05_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div class="bl_btnNum">
					<div @click="pageBack(5)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div @click="pageNext(5)" :class="[pageNum !== 2? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
			</div>
			<div v-if="tabState==6" >
				<div v-if="pageNum == 1">
					<div class="bl_pht06_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht06_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht06_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div v-if="pageNum == 2">
					<div class="bl_pht06_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ーっf{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht06_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht06_p01_sub02">
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
			<div v-if="tabState==7" >
				<div v-if="pageNum == 1">
					<div class="bl_pht07_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht07_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht07_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div v-if="pageNum == 2">
					<div class="bl_pht07_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ーっf{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht07_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht07_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
				</div>
				<div class="bl_btnNum">
					<div @click="pageBack(7)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div @click="pageNext(7)" :class="[pageNum !== 2? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
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
			imgTxt_m:false,
			imgTxt_01:false,
			imgTxt_02:false,
			photoState_m:false,
			photoState_01:false,
			photoState_02:false,
			mainPhoto:require('@/assets/stbHKD01.png'),
			subPhoto01:require('@/assets/stbHKD02.png'),
			subPhoto02:require('@/assets/stbHKD03.png'),
			popmainPhoto_l:'',
			popmainPhoto_r:'',
			Body:'x-t2',
			Renzu:'10-24',
			State:'F4',
			location:'函館ベイサイド店',
			location_r:'弘前公園前店',
			CameraData:{
				Body:['x-t2','x-Pro2'],
				Renzu:['10-24','16-80'],
				State:['F4'],
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
			LocationData:{
				stbLocation:[
					'函館ベイサイド店','弘前公園前店','鐘つき通り店','上野公園店','冠水公園店','スノーピーク店',
					'フライトオブドリーム店','浜松城公園店','二寧坂店','北野異人館店','道後温泉駅店',
					'出雲大社店','鹿児島店','沖縄本町店',
				]
			}
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
			else if(tab == 4)
			{
				this.backBtn = true
				this.nextBtn = false
				this.pageNum -=1
				this.mainPhoto = this.PhotoData.stbFOD[0]
				this.subPhoto01 = this.PhotoData.stbFOD[1]
				this.subPhoto02 = this.PhotoData.stbFOD[2]
				this.location = this.LocationData.stbLocation[2]
			}
			else if(tab == 5)
			{
				this.backBtn = true
				this.nextBtn = false
				this.pageNum -=1
				this.mainPhoto = this.PhotoData.stbNNZ[0]
				this.subPhoto01 = this.PhotoData.stbNNZ[1]
				this.subPhoto02 = this.PhotoData.stbNNZ[2]
				this.location = this.LocationData.stbLocation[2]
			}
			else if(tab == 6)
			{
				this.backBtn = true
				this.nextBtn = false
				this.pageNum -=1
				this.mainPhoto = this.PhotoData.stbIZM[0]
				this.subPhoto01 = this.PhotoData.stbIZM[1]
				this.subPhoto02 = this.PhotoData.stbIZM[2]
				this.location = this.LocationData.stbLocation[2]
			}
			else if(tab == 7)
			{
				this.backBtn = true
				this.nextBtn = false
				this.pageNum -=1
				this.mainPhoto = this.PhotoData.stbKGM[0]
				this.subPhoto01 = this.PhotoData.stbKGM[1]
				this.subPhoto02 = this.PhotoData.stbKGM[2]
				this.location = this.LocationData.stbLocation[2]
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
			else if(tab == 4)
			{
				if(this.pageNum == 1)
				{
					this.backBtn = false
					this.nextBtn = true
					this.pageNum +=1
					this.mainPhoto = this.PhotoData.stbHMM[0]
					this.subPhoto01 = this.PhotoData.stbHMM[1]
					this.subPhoto02 = this.PhotoData.stbHMM[2]
					this.location = this.LocationData.stbLocation[3]
				}
			}
			else if(tab == 5)
			{
				if(this.pageNum == 1)
				{
					this.backBtn = false
					this.nextBtn = true
					this.pageNum +=1
					this.mainPhoto = this.PhotoData.stbKTN[0]
					this.subPhoto01 = this.PhotoData.stbKTN[1]
					this.subPhoto02 = this.PhotoData.stbKTN[2]
					this.location = this.LocationData.stbLocation[7]
				}
			}
			else if(tab == 6)
			{
				if(this.pageNum == 1)
				{
					this.backBtn = false
					this.nextBtn = true
					this.pageNum +=1
					this.mainPhoto = this.PhotoData.stbDGO[0]
					this.subPhoto01 = this.PhotoData.stbDGO[1]
					this.subPhoto02 = this.PhotoData.stbDGO[2]
					this.location = this.LocationData.stbLocation[9]
				}
			}
			else if(tab == 7)
			{
				if(this.pageNum == 1)
				{
					this.backBtn = false
					this.nextBtn = true
					this.pageNum +=1
					this.mainPhoto = this.PhotoData.stbOKW[0]
					this.subPhoto01 = this.PhotoData.stbOKW[1]
					this.subPhoto02 = this.PhotoData.stbOKW[2]
					this.location = this.LocationData.stbLocation[11]
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
			else if(tab == 4)
			{
				this.tabState =4
				this.tabCheck =4
				this.pageNum = 1
				this.mainPhoto = this.PhotoData.stbFOD[0]
				this.subPhoto01 = this.PhotoData.stbFOD[1]
				this.subPhoto02 = this.PhotoData.stbFOD[2]
				this.location = this.LocationData.stbLocation[6]
			}
			else if(tab == 5)
			{
				this.tabState =5
				this.tabCheck =5
				this.pageNum = 1
				this.mainPhoto = this.PhotoData.stbNNZ[0]
				this.subPhoto01 = this.PhotoData.stbNNZ[1]
				this.subPhoto02 = this.PhotoData.stbNNZ[2]
				this.location = this.LocationData.stbLocation[8]
			}
			else if(tab == 6)
			{
				this.tabState =6
				this.tabCheck =6
				this.pageNum = 1
				this.mainPhoto = this.PhotoData.stbIZM[0]
				this.subPhoto01 = this.PhotoData.stbIZM[1]
				this.subPhoto02 = this.PhotoData.stbIZM[2]
				this.location = this.LocationData.stbLocation[10]
			}
			else if(tab == 7)
			{
				this.tabState = 7
				this.tabCheck = 7
				this.pageNum = 1
				this.mainPhoto = this.PhotoData.stbOKW[0]
				this.subPhoto01 = this.PhotoData.stbOKW[1]
				this.subPhoto02 = this.PhotoData.stbOKW[2]
				this.location = this.LocationData.stbLocation[13]
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
	outline: none;
}
.bl_btn{
	position: absolute;
	top: 0;
	left: 0;

}
.bl_mainCont{
	position: absolute;
	width: 100%;
	height: 100%;
}
.page-l{
	position: absolute;
	top: 2%;
	z-index: 1;
	width: 50%;
height: 100%;
}
.page-r{
	position: absolute;
	top: 0%;
	right: 0;
	z-index: 1;
	width: 50%;
	height: 100%;
	border-left: 1px dotted rgb(110, 76, 25);
}
.el_btn{
	display: inline-block;
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
	height: 45%;
	z-index: 1;
}
.bl_pht02_p01_sub01{
	position: absolute;
	left: 55%;
	top: 30%;
	width: 30%;
	height: 30%;
	z-index: 1;
}
.bl_pht02_p01_sub02{
	position: absolute;
	left: 60%;
	top: 60%;
	width: 30%;
	height: 30%;
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

.bl_pht04_p01_m{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 45%;
	z-index: 1;
}
.bl_pht04_p01_sub01{
	position: absolute;
	left: 55%;
	top: 30%;
	width: 30%;
	height: 30%;
	z-index: 1;
}
.bl_pht04_p01_sub02{
	position: absolute;
	left: 60%;
	top: 60%;
	width: 30%;
	height: 30%;
	z-index: 1;
}

.bl_pht05_p01_m{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 45%;
	z-index: 1;
}
.bl_pht05_p01_sub01{
	position: absolute;
	left: 55%;
	top: 30%;
	width: 30%;
	height: 30%;
	z-index: 1;
}
.bl_pht05_p01_sub02{
	position: absolute;
	left: 60%;
	top: 60%;
	width: 30%;
	height: 30%;
	z-index: 1;
}

.bl_pht06_p01_m{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 45%;
	z-index: 1;
}
.bl_pht06_p01_sub01{
	position: absolute;
	left: 55%;
	top: 30%;
	width: 30%;
	height: 30%;
	z-index: 1;
}
.bl_pht06_p01_sub02{
	position: absolute;
	left: 60%;
	top: 60%;
	width: 30%;
	height: 30%;
	z-index: 1;
}

.bl_pht07_p01_m{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 45%;
	z-index: 1;
}
.bl_pht07_p01_sub01{
	position: absolute;
	left: 55%;
	top: 30%;
	width: 30%;
	height: 30%;
	z-index: 1;
}
.bl_pht07_p01_sub02{
	position: absolute;
	left: 60%;
	top: 60%;
	width: 30%;
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

.bl_pht02_m_r{
	position: absolute;
	left: 15%;
	top: 55%;
	width: 50%;
	height: 40%;
	z-index: 1;
}
.bl_pht02_sub01_r{
	position: absolute;
	left: 55%;
	top: 10%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht02_sub02_r{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 30%;
	z-index: 1;
}

.bl_pht03_m_l{
	position: absolute;
	left: 10%;
	top: 5%;
	width: 80%;
	height: 45%;
	z-index: 1;
}
.bl_pht03_sub01_l{
	position: absolute;
	left: 55%;
	top: 50%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht03_sub02_l{
	position: absolute;
	left: 10%;
	top: 60%;
	width: 40%;
	height: 30%;
	z-index: 1;
}
.bl_pht03_m_r{
	position: absolute;
	left: 15%;
	top: 55%;
	width: 50%;
	height: 40%;
	z-index: 1;
}
.bl_pht03_sub01_r{
	position: absolute;
	left: 55%;
	top: 10%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht03_sub02_r{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 30%;
	z-index: 1;
}

.bl_pht04_m_l{
	position: absolute;
	left: 10%;
	top: 5%;
	width: 80%;
	height: 45%;
	z-index: 1;
}
.bl_pht04_sub01_l{
	position: absolute;
	left: 55%;
	top: 50%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht04_sub02_l{
	position: absolute;
	left: 10%;
	top: 60%;
	width: 40%;
	height: 30%;
	z-index: 1;
}
.bl_pht04_m_r{
	position: absolute;
	left: 15%;
	top: 55%;
	width: 50%;
	height: 40%;
	z-index: 1;
}
.bl_pht04_sub01_r{
	position: absolute;
	left: 55%;
	top: 10%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht04_sub02_r{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 30%;
	z-index: 1;
}

.bl_pht05_m_l{
	position: absolute;
	left: 10%;
	top: 5%;
	width: 80%;
	height: 45%;
	z-index: 1;
}
.bl_pht05_sub01_l{
	position: absolute;
	left: 55%;
	top: 50%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht05_sub02_l{
	position: absolute;
	left: 10%;
	top: 60%;
	width: 40%;
	height: 30%;
	z-index: 1;
}
.bl_pht05_m_r{
	position: absolute;
	left: 15%;
	top: 55%;
	width: 50%;
	height: 40%;
	z-index: 1;
}
.bl_pht05_sub01_r{
	position: absolute;
	left: 55%;
	top: 10%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht05_sub02_r{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 30%;
	z-index: 1;
}

.bl_pht06_m_l{
	position: absolute;
	left: 10%;
	top: 5%;
	width: 80%;
	height: 45%;
	z-index: 1;
}
.bl_pht06_sub01_l{
	position: absolute;
	left: 55%;
	top: 50%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht06_sub02_l{
	position: absolute;
	left: 10%;
	top: 60%;
	width: 40%;
	height: 30%;
	z-index: 1;
}
.bl_pht06_m_r{
	position: absolute;
	left: 15%;
	top: 55%;
	width: 50%;
	height: 40%;
	z-index: 1;
}
.bl_pht06_sub01_r{
	position: absolute;
	left: 55%;
	top: 10%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht06_sub02_r{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 30%;
	z-index: 1;
}

.bl_pht07_m_l{
	position: absolute;
	left: 10%;
	top: 5%;
	width: 80%;
	height: 45%;
	z-index: 1;
}
.bl_pht07_sub01_l{
	position: absolute;
	left: 55%;
	top: 50%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht07_sub02_l{
	position: absolute;
	left: 10%;
	top: 60%;
	width: 40%;
	height: 30%;
	z-index: 1;
}
.bl_pht07_m_r{
	position: absolute;
	left: 15%;
	top: 55%;
	width: 50%;
	height: 40%;
	z-index: 1;
}
.bl_pht07_sub01_r{
	position: absolute;
	left: 55%;
	top: 10%;
	width: 35%;
	height: 40%;
	z-index: 1;
}
.bl_pht07_sub02_r{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 30%;
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
	color:rgba(0, 0, 0, 0.425);
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
	text-align: 
	center;
}


button{
	border: none;
	background: none;
	outline: none;
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