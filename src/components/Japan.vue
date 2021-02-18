<template>
	<div class="ly">
		<div class="bl_pop" v-if="isPop">
			<button @click="popOff()" class="el_pop_btn">✖︎</button>
			<div class="bl_pop_l" >
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
					<p class="el_pop_pointTtl_cont">{{point}}</p>
				</div>
			</div>
		</div>
		<div class="bl_btn">
			<p :class="[tabCheck== 1? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(1)">北海道</p>
			<p :class="[tabCheck== 2? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(2)">東北</p>
			<p :class="[tabCheck== 3? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(3)">関東</p>
			<p :class="[tabCheck== 4? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(4)">甲信越</p>
			<p :class="[tabCheck== 5? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(5)">北陸</p>
			<p :class="[tabCheck== 6? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(6)">東海</p>
			<p :class="[tabCheck== 7? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(7)">関西</p>
			<p :class="[tabCheck== 8? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(8)">中国</p>
			<p :class="[tabCheck== 9? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(9)">四国</p>
			<p :class="[tabCheck== 10? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(10)">九州</p>
			<p :class="[tabCheck== 11? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(11)">沖縄</p>
		</div>
		<div v-if="tabState==1" >
			<div class="bl_page_cont" v-if="pageNum == 1">
					<div class="bl_pht01_p01_m01">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0,false),emitData(1,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p>
						</div>
					</div>
					<div class="bl_pht01_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht01_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(1,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 2">
					<div class="bl_pht01_p02_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0),emitData(1,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 3">
					<div class="bl_pht01_p03_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0),emitData(1,3,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht01_p03_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(1,3,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_btnNum">
					<div @click="back(1)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div :class="[pageNum == 3? 'onCircle': 'circle']" >3</div>
					<div @click="next(1)" :class="[pageNum !== 3? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
		</div>
		<div v-if="tabState==2" >
			<div class="bl_page_cont" v-if="pageNum == 1">
					<div class="bl_pht02_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(2,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht02_p01_sub01">
						<img :class="[photoState_01? 'el_img_ver_js': 'el_img_ver']" @click="isUP(1,false),emitData(2,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 2">
					<div class="bl_pht02_p02_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(2,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht02_p02_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(2,2,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 3">
					<div class="bl_pht02_p03_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(2,3,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht02_p03_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(2,3,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht02_p03_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(2,3,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_btnNum">
					<div @click="back(2)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div :class="[pageNum == 3? 'onCircle': 'circle']" >3</div>
					<div @click="next(2)" :class="[pageNum !== 3? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
		</div>
		<div v-if="tabState==3" >
			<div class="bl_page_cont" v-if="pageNum == 1">
					<div class="bl_pht03_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(3,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht03_p01_sub01">
						<img :class="[photoState_01? 'el_img_ver_js': 'el_img_ver']" @click="isUP(1),emitData(3,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht03_p01_sub02">
						<img :class="[photoState_02? 'el_img_ver_js': 'el_img_ver']" @click="isUP(2),emitData(3,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 2">
					<div class="bl_pht03_p02_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(3,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht03_p02_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1,false),emitData(3,2,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht03_p02_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2,false),emitData(3,2,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 3">
					<div class="bl_pht03_p03_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(3,3,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht03_p03_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1,false),emitData(3,3,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht03_p03_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(3,3,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 4">
					<div class="bl_pht03_p04_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(3,4,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht03_p04_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1,false),emitData(3,4,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_btnNum">
					<div @click="back(3)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div :class="[pageNum == 3? 'onCircle': 'circle']">3</div>
					<div :class="[pageNum == 4? 'onCircle': 'circle']" >4</div>
					<div @click="next(3)" :class="[pageNum !== 4? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
		</div>
		<div v-if="tabState== 4" >
			<div class="bl_page_cont" v-if="pageNum == 1">
					<div class="bl_pht04_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(4,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht04_p01_sub01">
						<img :class="[photoState_01? 'el_img_ver_js': 'el_img_ver']" @click="isUP(1),emitData(4,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 2">
					<div class="bl_pht04_p02_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0,false),emitData(4,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht04_p02_sub01">
						<img :class="[photoState_01? 'el_img_ver_js': 'el_img_ver']" @click="isUP(1),emitData(4,2,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht04_p02_sub02">
						<img :class="[photoState_02? 'el_img_ver_js': 'el_img_ver']" @click="isUP(2,false),emitData(4,2,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_btnNum">
					<div @click="back(4)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div @click="next(4)" :class="[pageNum !== 2? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
		</div>
		<div v-if="tabState== 5" >
			<div class="bl_page_cont" v-if="pageNum == 1">
					<div class="bl_pht05_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(5,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht05_p01_sub01">
						<img :class="[photoState_01? 'el_img_ver_js': 'el_img_ver']" @click="isUP(1),emitData(5,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 2">
					<div class="bl_pht05_p02_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0),emitData(5,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht05_p02_sub01">
						<img :class="[photoState_01? 'el_img_ver_js': 'el_img_ver']" @click="isUP(1,false),emitData(5,2,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_btnNum">
					<div @click="back(5)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div @click="next(5)" :class="[pageNum !== 2? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
		</div>
		<div v-if="tabState== 6" >
			<div class="bl_page_cont" v-if="pageNum == 1">
					<div class="bl_pht06_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(6,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht06_p01_sub01">
						<img :class="[photoState_01? 'el_img_ver_js': 'el_img_ver']" @click="isUP(1),emitData(6,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 2">
					<div class="bl_pht06_p02_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0),emitData(6,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht06_p02_sub01">
						<img :class="[photoState_01? 'el_img_ver_js': 'el_img_ver']" @click="isUP(1),emitData(6,2,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_btnNum">
					<div @click="back(6)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div @click="next(6)" :class="[pageNum !== 2? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
		</div>
		<div v-if="tabState== 7" >
			<div class="bl_page_cont" v-if="pageNum == 1">
					<div class="bl_pht07_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(7,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht07_p01_sub01">
						<img :class="[photoState_01? 'el_img_ver_js': 'el_img_ver']" @click="isUP(1,false),emitData(7,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 2">
					<div class="bl_pht07_p02_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0),emitData(7,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht07_p02_sub01">
						<img :class="[photoState_01? 'el_img_ver_js': 'el_img_ver']" @click="isUP(1,false),emitData(7,2,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht07_p02_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(7,2,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP(3)">詳細をみる</button>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 3">
					<div class="bl_pht07_p03_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0,false),emitData(7,3,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht07_p03_sub01">
						<img :class="[photoState_01? 'el_img_ver_js': 'el_img_ver']" @click="isUP(1,false),emitData(7,3,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_btnNum">
					<div @click="back(7)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div :class="[pageNum == 3? 'onCircle': 'circle']">3</div>
					<div @click="next(7)" :class="[pageNum !== 3? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
		</div>
		<div v-if="tabState== 8" >
			<div class="bl_page_cont" v-if="pageNum == 1">
					<div class="bl_pht08_p01_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0),emitData(8,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht08_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(8,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 2">
					<div class="bl_pht08_p02_m">
						<img :class="[photoState_? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(8,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht08_p02_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(8,2,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 3">
					<div class="bl_pht08_p03_m">
						<img :class="[photoState_? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(8,3,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht08_p03_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(8,3,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_btnNum">
					<div @click="back(8)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div :class="[pageNum == 3? 'onCircle': 'circle']" >3</div>
					<div @click="next(8)" :class="[pageNum !== 3? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
		</div>
		<div v-if="tabState== 9" >
			<div class="bl_page_cont" v-if="pageNum == 1">
					<div class="bl_pht09_p01_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0),emitData(9,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht09_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(9,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht09_p01_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(9,1,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 2">
					<div class="bl_pht09_p02_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0),emitData(9,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht09_p02_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(9,2,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht09_p02_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(9,2,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
							<button class="el_img_popTxt" @click="isUP(3)">詳細をみる</button>
						</div>
					</div>
			</div>
			<div class="bl_btnNum">
					<div @click="back(9)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div @click="next(9)" :class="[pageNum !== 2? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
		</div>
		<div v-if="tabState== 10" >
			<div class="bl_page_cont" v-if="pageNum == 1">
					<div class="bl_pht010_p01_m">
						<img :class="[photoState_m? 'el_img_hor_js': 'el_img_hor']" @click="isUP(0),emitData(10,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht010_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1,false),emitData(10,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location01}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 2">
					<div class="bl_pht010_p02_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0),emitData(10,2,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht010_p02_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(10,2,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_page_cont" v-if="pageNum == 3">
					<div class="bl_pht010_p03_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0,false),emitData(10,3,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht010_p03_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(10,3,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location02}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht010_p03_sub02">
						<img :class="[photoState_02? 'el_img_hor_js': 'el_img_hor']" @click="isUP(2),emitData(10,3,3)" v-on:mouseover="u(2)" v-on:mouseleave="out(2)" :src="subPhoto02">
						<p class="el_pht_txt" v-show="imgTxt_02">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location03}}ー</p><br>
						</div>
					</div>
			</div>
			<div class="bl_btnNum">
					<div @click="back(10)" :class="[pageNum !== 1? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="backBtn">前のページへ</div>
					<div :class="[pageNum == 1? 'onCircle': 'circle']">1</div>
					<div :class="[pageNum == 2? 'onCircle': 'circle']">2</div>
					<div :class="[pageNum == 3? 'onCircle': 'circle']">3</div>
					<div @click="next(10)" :class="[pageNum !== 3? 'el_imgNum_txt_js': 'el_imgNum_txt_def']" :disable="nextBtn">次のページへ</div>
			</div>
		</div>
		<div v-if="tabState== 11" >
			<div class="bl_page_cont" v-if="pageNum == 1">
					<div class="bl_pht011_p01_m">
						<img :class="[photoState_m? 'el_img_ver_js': 'el_img_ver']" @click="isUP(0),emitData(11,1,1)" v-on:mouseover="u(0)" v-on:mouseleave="out(0)" :src="mainPhoto">
						<p class="el_pht_txt" v-show="imgTxt_m">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
						</div>
					</div>
					<div class="bl_pht011_p01_sub01">
						<img :class="[photoState_01? 'el_img_hor_js': 'el_img_hor']" @click="isUP(1),emitData(11,1,2)" v-on:mouseover="u(1)" v-on:mouseleave="out(1)" :src="subPhoto01">
						<p class="el_pht_txt" v-show="imgTxt_01">詳細をみる</p>
						<div class="bl_imgTxt">
							<p class="el_img_posTxt">ー{{location}}ー</p><br>
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
			isPop:false,
			popState:true,
			tabCheck:1,
			tabState:1,
			photoState_m:false,
			photoState_01:false,
			photoState_02:false,
			imgTxt_m:false,
			imgTxt_01:false,
			imgTxt_02:false,
			NumM:'',
			Numl:'',
			Numr:'',
			pageNum:1,
			pageState:1,
			backBtn:true,
			nextBtn:false,
			isPart:0,
			isNum:0,
			isShow:false,
			popmainPhoto:'',
			mainPhoto:require('@/assets/japanHKD_SOYm.png'),
			subPhoto01:require('@/assets/japanHKD_SOY01.png'),
			subPhoto02:require('@/assets/japanHKD_SOY02.png'),
			Body:'x-t2',
			Renzu:'10-24',
			State:'F4',
			Ref:'',
			location:'宗谷岬',
			CameraData:{
				Body:['x-t2','x-Pro2','iPhone'],
				Renzu:['10-24m F4','16-80m F4','35m F1.4'],
			},
			PhotoData:{
				japanHKD: [
					require('@/assets/japanHKD_SOYm.png'),
					require('@/assets/japanHKD_SOY01.png'),
					require('@/assets/japanHKD_SOY02.png'),
					require('@/assets/japanBEI01.png'),
					require('@/assets/japanHKD01.png'),
					require('@/assets/japanHKD_HKD01.png'),
				],
				japanTHK:[
					require('@/assets/japanTHK_HRSm.png'),
					require('@/assets/japanTHK_HRS02.png'),
					require('@/assets/japanTHK_IWTm.png'),
					require('@/assets/japanTHK_IWT01.png'),
					require('@/assets/japanTHK_NGTm.png'),
					require('@/assets/japanTHK_NGT01.png'),
					require('@/assets/japanTHK_NGT02.png'),
				],
				japanKNT:[
					require('@/assets/japanKNT_IBGm.png'),
					require('@/assets/japanKNT_IBG01.png'),
					require('@/assets/japanKNT_IBG02.png'),
					require('@/assets/japanKNT_TTGm.png'),
					require('@/assets/japanKNT_TTG01.png'),
					require('@/assets/japanKNT_TTG02.png'),
					require('@/assets/japanKNT_STM02.png'),
					require('@/assets/japanKNT_STM01.png'),
					require('@/assets/japanKNT_STMm.png'),
					require('@/assets/japanKNT_KNWm.png'),
					require('@/assets/japanKNT_KNW01.png'),
				],
				japanKSE:[
					require('@/assets/japanKSE_NGNm.png'),
					require('@/assets/japanKSE_NGN01.png'),
					require('@/assets/japanKSE_YMNm.png'),
					require('@/assets/japanKSE_YMN01.png'),
					require('@/assets/japanKSE_YMN02.png'),
					require('@/assets/japanTHK_NGTm.png'),
					require('@/assets/japanTHK_NGT01.png'),
					require('@/assets/japanTHK_NGT02.png'),
				],
				japanHKR:[
					require('@/assets/japanHKR_FKIm.png'),
					require('@/assets/japanHKR_FKI01.png'),
					require('@/assets/japanHKR_KNZm.png'),
					require('@/assets/japanHKR_KNZ01.png'),
				],
				japanTKI:[
					require('@/assets/japanTKI_MIEm.png'),
					require('@/assets/japanTKI_MIE01.png'),
					require('@/assets/japanTKI_GIFm.png'),
					require('@/assets/japanTKI_GIF01.png'),
				],
				japanKNK:[
					require('@/assets/japanKNK_NARm.png'),
					require('@/assets/japanKNK_NAR01.png'),
					require('@/assets/japanKNK_KYOm.png'),
					require('@/assets/japanKNK_KYO01.png'),
					require('@/assets/japanKNK_KYO02.png'),
					require('@/assets/japanKNK_OSKm.png'),
					require('@/assets/japanKNK_OSK01.png'),
				],
				japanCGK:[
					require('@/assets/japanCGK_HRMm.png'),
					require('@/assets/japanCGK_HRM02.png'),
					require('@/assets/japanCGK_TTRm.png'),
					require('@/assets/japanCGK_TTR01.png'),
					require('@/assets/japanCGK_SMNm.png'),
					require('@/assets/japanCGK_SMN01.png'),
				],
				japanSKK:[
					require('@/assets/japanSKK_EHMm.png'),
					require('@/assets/japanSKK_EHM01.png'),
					require('@/assets/japanSKK_EHM02.png'),
					require('@/assets/japanSKK_KGWm.png'),
					require('@/assets/japanSKK_KGW01.png'),
					require('@/assets/japanSKK_KGW02.png'),
				],
				japanKSY:[
					require('@/assets/japanKSY_KGMm.png'),
					require('@/assets/japanKSY_KMMm.png'),
					require('@/assets/japanKSY_BPPm.png'),
					require('@/assets/japanKSY_BPP01.png'),
					require('@/assets/japanKSY_BPP02.png'),
					require('@/assets/japanKSY_SAGm.png'),
					require('@/assets/japanKSY_NGSm.png'),
					require('@/assets/japanKSY_FKOm.png'),
				],
				japanOKW:[
					require('@/assets/japanOKW_OKW02.png'),
					require('@/assets/japanOKW_OKW01.png'),
				],
			},
			LocationData:{
				japanHKD:[
					'宗谷岬','美瑛町','函館山'
				],
				japanTHK:[
					'弘前城','陸前高田','清津峡'
				],
				japanKNT:[
					'日立駅','日光東照宮','川越市','江ノ島'
				],
				japanKSE:[
					'妻籠宿','河口湖','清津峡'
				],
				japanHKR:[
					'東尋坊','茶屋町'
				],
				japanTKI:[
					'伊勢神宮','白川郷'
				],
				japanKNK:[
					'奈良公園','二寧坂','通天閣'
				],
				japanCGK:[
					'原爆ドーム','鳥取砂丘','出雲大社'
				],
				japanSKK:[
					'下灘駅','高屋神社',
				],
				japanKSY:[
					'城山展望所','熊本城','別府温泉','大魚神社','稲佐山','門司港駅'
				],
				japanOKW:[
					'美ら海水族館'
				]
			},
			mind:'f',
			PointData:{
				japanHKD:[
					'日の丸構図を意識してモニュメンを主役に。最果て感を出すために海をいれるべきだった。',
					'余白を意識して看板を主役に。白と赤のコントラスがポイント',
					'銅像を主役に斜めから。視線の先にサブのモニュメンを設置',
					'全体の７割の雪の夜空を主役に。あえてライトアップ部分はサブに設置',
					'全体の７割の雪の夜空を主役に。雪の量が多すぎたのが反省点',
					'全体の７割の雪の夜空を主役に。人を入れて夜景の主役を際立たせるべきだった'
				],
				japanTHK:[
					'中心の川を主役に。雪の量が多すぎたのが反省点',
					'古い時計と雪の夜空を主役に。建物全体の情報量が少なすぎたのが反省点',
					'松の木を人の視線を活かして主役に。画角を広げて人の写っている割合が少ないのが反省点',
					'津波の発生源である地平線を主役に。モニュメントの割合が高すぎたので空と海の割合を増やすべきだった',
					'日の丸構図でトンネルを主役に。白飛びが起きていたので光量の調整が足りないのが反省点',
					'日の丸構図でトンネルを主役に',
					'トンネルの奥行きを主役に。焦点を手前に'
				],
				japanKNT:[
					'手間の柱を入れて奥いきを出して建築物を主役に。余白をいれることによって主役をより際立たせることが出来た',
					'光量を調整して雑多の人々を主役に。SSを落として人の動きをいれるべきだった',
					'朝日に当たるピアノを主役に。逆光の中で主役の黒いものに光量が足りなさすぎた',
					'視線を用いて建築物を主役に。人の」割合が高すぎて主役のが際立ちさが足りない',
					'低コントラスト階段に高コントラスのアクセントのカラーを持つ人を主役に',
					'縦構図で家紋を主役に',
					'乗り物を手前に入れて主役に。全体に焦点が当たっているため主役がわかりにくい',
					'建築物に対する視線を主役に。光量が足りずブレやノイズが増えてしまった',
					'文字を活かして人を主役に。',
					'江ノ島と人を主役に。白飛びが激しいので光量の調整不足',
					'あえて逆光で人を主役に。',
				],
				japanKSE:[
					'光の向きをずらし人を主役に。火から出る煙の量の調整不足',
					'斜めからの光の当たる先を主役に。',
					'日の丸構図で鳥居を主役に。画角を広げて空間を広げるべきだった',
					'視線を活かして犬を主役に。画角が狭くなり富士山を入れきれなかった',
					'富士山を背景に働く人を主役に。室内のため光量が足りなくなってしまった',
				],
				japanHKR:[
					'地平線と波を主役に。撮影位置が低くして海と空の割合が増やすべきだった',
					'地平線への視線を活かして崖を主役に。',
					'古い建築物の中の高コントラストの人を主役に。余計な人がいないタイミングでの撮影が必要だった',
					'手前に柱を入れて窓際の席を主役に。',
				],
				japanTKI:[
					'逆光を活かして鳥居を主役に。太陽の位置と人の位置の調整不足',
					'人を活かして手前の食べ物を主役に。箸をオボンの手前においてオボンの情報量を減らすべきだった',
					'人形を活かして建築物を主役に。画角が広げて人形を全ていれるべきだった',
					'建物内の光を活かして夜の建築物を主役に。窓からの人の影をいれることが出来たら完璧だった',
				],
				japanKNK:[
					'日の丸構図で人と動物を主役に。人の視線と動物の視線を要検討',
					'縦構図で手前をぼかし奥の鹿を主役に。右端から光もよかった',
					'建築物と人を対象において主役に。長時間露光でによる光量調整が不十分',
					'建築物を活かしてのれんを主役に。のれんが折れ曲がるなどアクセントが足りない',
					'低コントラストの街並みや人通りの高コントラスの人を主役に。人の数が多すぎて主役の引き立てが不十分に',
					'三分割でコントラスを揃え手前の人を主役に。撮影位置をもう少し下げて建物の全景を入れるべきだった',
					'視線と背景を活かして手前の人を主役に。主役以外の人が多い方が主役の人がより引き立てられるはずだ',
				],
				japanCGK:[
					'手前の運転席を活かして車内からの景色を主役に。手前の運転席をボケすぎた。もう少し絞るべきだった',
					'建築物を活かして鉄道を主役に。',
					'砂漠の割合を９割にして人を主役に。',
					'人を活かして坂を主役に。青空のコントラスがあればよかった',
					'日の丸構図を人を主役に。主役と背景が短調であり他の要素を入れるべきだった',
					'建築物を切り取り人を歩く人を主役に。',
				],
				japanSKK:[
					'影と日光を活かして駅舎を主役に。駅の画角をもう少し広げるべき',
					'運転者の視線を活かして車両を主役に。視線の余白が足りない',
					'広角レンズを活かして手前を主役に。',
					'夕日を活かして鳥居を主役に。人のアクセントが欲しい',
					'青空を活かして鳥居を主役に。人のアクセントが足りない',
					'鳥居と視線を活かした人を主役に。階段の高さを活かしたアクセントが欲しい',
				],
				japanKSY:[
					'日の丸構図と視線で人を主役に。日の丸構図でなく高さを上げて人の割合を下げるべきだった',
					'建築物を切り取り人を歩く人を主役に。',
					'湯気と地名を活かして温泉を主役に。広角を広げ岩の面積を下げるべきだった',
					'人を設置して湯気を主役に。',
					'視線と看板を活かして人を主役に。同系統の鉄道が停車していたら完璧だった',
					'石の道を活かして歩く人を主役に。',
					'人を活かして夜景を主役に。人の割合が広すぎた',
				],
				japanOKW:[
					'人とスマホを活かして動物を主役に。',
					'周辺光量を」落として真ん中の魚を主役に。別系統の魚の大群であればよりよかった'
				]
			}
		}
	},
	methods:{
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
		popOff(){
			this.isPop =false
			this.popState = true
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
		emitData(tabNum,pageNum,photoNum){
			if(tabNum == 1)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKD[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKD[1]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKD[2]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKD[3]
					}
				}
				else if(pageNum == 3)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKD[4]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKD[5]
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
						this.point = this.PointData.japanTHK[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanTHK[1]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanTHK[2]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanTHK[3]
					}
				}
				else if(pageNum == 3)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanTHK[4]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanTHK[5]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanTHK[6]
					}
				}
			}
			else if(tabNum == 3)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNT[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNT[1]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNT[2]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNT[3]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNT[4]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNT[5]
					}
				}
				else if(pageNum == 3)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNT[6]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNT[7]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNT[8]
					}
				}
				else if(pageNum == 4)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNT[9]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNT[10]
					}
				}
			}
			else if(tabNum == 4)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKSE[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKSE[1]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKSE[2]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKSE[3]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKD[4]
					}
				}
			}
			else if(tabNum == 5)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKR[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKR[1]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKR[2]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKR[3]
					}
				}
			}
			else if(tabNum == 6)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanTKI[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanTKI[1]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanTKI[2]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanTKI[3]
					}
				}
			}
			else if(tabNum == 7)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNK[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNK[1]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNK[2]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNK[3]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNK[4]
					}
				}
				else if(pageNum == 3)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNK[5]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKNK[6]
					}
				}
			}
			else if(tabNum == 8)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanCGK[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanCGK[1]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanCGK[2]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanCGK[3]
					}
				}
				else if(pageNum == 3)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanCGK[4]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanCGK[5]
					}
				}
			}
			else if(tabNum == 9)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanSKK[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanSKK[1]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanSKK[2]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanSKK[3]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanSKK[4]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanSKK[5]
					}
				}
			}
			else if(tabNum == 10)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKSY[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKSY[1]
					}
				}
				else if(pageNum == 2)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKYU[2]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKSY[3]
					}
				}
				else if(pageNum == 3)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKSY[4]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKSY[5]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanKSY[6]
					}
				}
			}
			else if(tabNum == 11)
			{
				if(pageNum == 1)
				{
					if(photoNum == 1)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanOKW[0]
					}
					else if(photoNum == 2)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanOKW[1]
					}
					else if(photoNum == 3)
					{
						this.Body = this.CameraData.Body[0]
						this.Renzu = this.CameraData.Renzu[1]
						this.point = this.PointData.japanHKD[1]
					}
				}
			}
		},
		changeTab(tab)
		{
			if(tab == 1){
				this.tabState = 1
				this.tabCheck = 1
				this.pageNum = 1
				this.mainPhoto= this.PhotoData.japanHKD[0]
				this.subPhoto01 = this.PhotoData.japanHKD[1]
				this.subPhoto02 = this.PhotoData.japanHKD[2]
				this.location = this.LocationData.japanHKD[0]
				this.Body = this.CameraData.Body[0]
				this.Renzu = this.CameraData.Renzu[0]
			}
			else if(tab == 2)
			{
				this.tabState = 2
				this.tabCheck = 2
				this.pageNum = 1
				this.mainPhoto= this.PhotoData.japanTHK[0]
				this.subPhoto01 = this.PhotoData.japanTHK[1]
				this.location = this.LocationData.japanTHK[0]
			}
			else if(tab == 3)
			{
				this.tabState = 3
				this.tabCheck = 3
				this.pageNum = 1
				this.mainPhoto= this.PhotoData.japanKNT[0]
				this.subPhoto01 = this.PhotoData.japanKNT[1]
				this.subPhoto02 = this.PhotoData.japanKNT[2]
				this.location = this.LocationData.japanKNT[0]
			}
			else if(tab == 4)
			{
				this.tabState =4
				this.tabCheck =4
				this.pageNum = 1
				this.mainPhoto= this.PhotoData.japanKSE[0]
				this.subPhoto01 = this.PhotoData.japanKSE[1]
				this.location = this.LocationData.japanKSE[0]
			}
			else if(tab == 5)
			{
				this.tabState = 5
				this.tabCheck = 5
				this.pageNum = 1
				this.mainPhoto= this.PhotoData.japanHKR[0]
				this.subPhoto01 = this.PhotoData.japanHKR[1]
				this.location = this.LocationData.japanHKR[0]
			}
			else if(tab == 6)
			{
				this.tabState = 6
				this.tabCheck = 6
				this.pageNum = 1
				this.mainPhoto= this.PhotoData.japanTKI[0]
				this.subPhoto01 = this.PhotoData.japanTKI[1]
				this.location = this.LocationData.japanTKI[0]
			}
			else if(tab == 7)
			{
				this.tabState = 7
				this.tabCheck = 7
				this.pageNum = 1
				this.mainPhoto= this.PhotoData.japanKNK[0]
				this.subPhoto01 = this.PhotoData.japanKNK[1]
				this.location = this.LocationData.japanKNK[0]
			}
			else if(tab == 8)
			{
				this.tabState = 8
				this.tabCheck = 8
				this.pageNum = 1
				this.mainPhoto= this.PhotoData.japanCGK[0]
				this.subPhoto01 = this.PhotoData.japanCGK[1]
				this.location = this.LocationData.japanCGK[0]
			}
			else if(tab == 9)
			{
				this.tabState = 9
				this.tabCheck = 9
				this.pageNum = 1
				this.mainPhoto= this.PhotoData.japanSKK[0]
				this.subPhoto01 = this.PhotoData.japanSKK[1]
				this.subPhoto02 = this.PhotoData.japanSKK[2]
				this.location = this.LocationData.japanSKK[0]
			}
			else if(tab == 10)
			{
				this.tabState = 10
				this.tabCheck = 10
				this.pageNum = 1
				this.mainPhoto= this.PhotoData.japanKSY[0]
				this.subPhoto01 = this.PhotoData.japanKSY[1]
				this.location = this.LocationData.japanKSY[0]
				this.location01 = this.LocationData.japanKSY[1]
			}
			else if(tab == 11)
			{
				this.tabState = 11
				this.tabCheck = 11
				this.pageNum = 1
				this.mainPhoto= this.PhotoData.japanOKW[0]
				this.subPhoto01 = this.PhotoData.japanOKW[1]
				this.location = this.LocationData.japanOKW[0]
			}
		},
		back(tab){
			if(tab == 1)
			{
				if(this.pageNum == 2)
				{
					this.backBtn = false
					this.nextBtn = true
					this.mainPhoto = this.PhotoData.japanHKD[0]
					this.location = this.LocationData.japanHKD[0]
					this.subPhoto01 = this.PhotoData.japanHKD[1]
					this.subPhoto02 = this.PhotoData.japanHKD[2]
					this.pageNum -=1
					this.backBtn = true
				}
				else if(this.pageNum == 3)
				{
					this.pageNum -=1
					this.mainPhoto = this.PhotoData.japanHKD[3]
					this.location = this.LocationData.japanHKD[1]
					this.nextBtn = true
				}
			}else if(tab == 2)
			{
				if(this.pageNum == 2)
				{
					this.backBtn = false
					this.nextBtn = true
					this.mainPhoto = this.PhotoData.japanTHK[0]
					this.location = this.LocationData.japanTHK[0]
					this.subPhoto01 = this.PhotoData.japanTHK[1]
					this.pageNum -=1
					this.backBtn = true
				}
				else if(this.pageNum == 3)
				{
					this.pageNum -=1
					this.mainPhoto = this.PhotoData.japanTHK[2]
					this.subPhoto01 = this.PhotoData.japanTHK[3]
					this.location = this.LocationData.japanTHK[1]
					this.nextBtn = true
				}
			}else if(tab == 3)
			{
				if(this.pageNum == 2)
				{
					this.mainPhoto = this.PhotoData.japanKNT[0]
					this.subPhoto01 = this.PhotoData.japanKNT[1]
					this.subPhoto02 = this.PhotoData.japanKNT[2]
					this.location = this.LocationData.japanKNT[0]
					this.pageNum -=1
					this.backBtn = true
				}
				else if(this.pageNum == 3)
				{
					this.pageNum -=1
					this.mainPhoto = this.PhotoData.japanKNT[3]
					this.subPhoto01 = this.PhotoData.japanKNT[4]
					this.subPhoto02 = this.PhotoData.japanKNT[5]
					this.location = this.LocationData.japanKNT[1]
				}
				else if(this.pageNum == 4)
				{
					this.pageNum -=1
					this.mainPhoto = this.PhotoData.japanKNT[6]
					this.subPhoto01 = this.PhotoData.japanKNT[7]
					this.location = this.LocationData.japanKNT[1]
					this.nextBtn = false
				}
			}else if(tab == 4)
			{
				if(this.pageNum == 2)
				{
					this.nextBtn = true
					this.mainPhoto = this.PhotoData.japanKSE[0]
					this.subPhoto01 = this.PhotoData.japanKSE[1]
					this.subPhoto02 = this.PhotoData.japanKSE[2]
					this.location = this.LocationData.japanKSE[0]
					this.pageNum -=1
					this.backBtn = true
				}
				else if(this.pageNum == 3)
				{
					this.pageNum -=1
					this.mainPhoto = this.PhotoData.japanKSE[3]
					this.subPhoto01 = this.PhotoData.japanKSE[4]
					this.subPhoto02 = this.PhotoData.japanKSE[5]
					this.location = this.LocationData.japanKSE[1]
					this.nextBtn = true
				}
			}
			else if(tab == 5)
			{
				if(this.pageNum == 2)
				{
					this.mainPhoto = this.PhotoData.japanHKR[0]
					this.subPhoto01 = this.PhotoData.japanHKR[1]
					this.location = this.LocationData.japanHKR[0]
					this.nextBtn = false
					this.backBtn = true
					this.pageNum -=1
				}
			}
			else if(tab == 6)
			{
				if(this.pageNum == 2)
				{
					this.mainPhoto = this.PhotoData.japanTKI[0]
					this.subPhoto01 = this.PhotoData.japanTKI[1]
					this.location = this.LocationData.japanTKI[0]
					this.nextBtn = false
					this.backBtn = true
					this.pageNum -=1
				}
			}
			else if(tab == 7)
			{
				if(this.pageNum == 2)
				{
					this.mainPhoto = this.PhotoData.japanKNK[0]
					this.subPhoto01 = this.PhotoData.japanKNK[1]
					this.location = this.LocationData.japanKNK[0]
					this.backBtn = true
					this.pageNum -=1
				}else if(this.pageNum == 3)
				{
					this.mainPhoto = this.PhotoData.japanKNK[2]
					this.subPhoto01 = this.PhotoData.japanKNK[3]
					this.subPhoto02 = this.PhotoData.japanKNK[4]
					this.location = this.LocationData.japanKNK[1]
					this.nextBtn = false
					this.pageNum -=1
				}
			}
			else if(tab == 8)
			{
				if(this.pageNum == 2)
				{
					this.mainPhoto = this.PhotoData.japanCGK[0]
					this.subPhoto01 = this.PhotoData.japanCGK[1]
					this.location = this.LocationData.japanCGK[0]
					this.location1 = this.LocationData.japanCGK[1]
					this.backBtn = true
					this.pageNum -=1
				}else if(this.pageNum == 3)
				{
					this.mainPhoto = this.PhotoData.japanCGK[2]
					this.subPhoto01 = this.PhotoData.japanCGK[3]
					this.location = this.LocationData.japanCGK[1]
					this.nextBtn = false
					this.pageNum -=1
				}
			}
			else if(tab == 9)
			{
				if(this.pageNum == 2)
				{
					this.mainPhoto = this.PhotoData.japanSKK[0]
					this.subPhoto01 = this.PhotoData.japanSKK[1]
					this.subPhoto02 = this.PhotoData.japanSKK[2]
					this.location = this.LocationData.japanSKK[0]
					this.nextBtn = false
					this.backBtn = true
					this.pageNum -=1
				}
			}
			else if(tab == 10)
			{
				if(this.pageNum == 2)
				{
					this.mainPhoto = this.PhotoData.japanKSY[0]
					this.subPhoto01 = this.PhotoData.japanKSY[1]
					this.location = this.LocationData.japanKSY[0]
					this.location01 = this.LocationData.japanKSY[1]
					this.backBtn = true
					this.pageNum -=1
				}else if(this.pageNum == 3)
				{
					this.mainPhoto = this.PhotoData.japanKSY[2]
					this.subPhoto01 = this.PhotoData.japanKSY[3]
					this.subPhoto02 = this.PhotoData.japanKSY[4]
					this.location = this.LocationData.japanKSY[2]
					this.nextBtn = false
					this.pageNum -=1
				}
			}
		},
		next(tab){
			if(tab == 1)
			{
				if(this.pageNum == 1)
				{
					this.backBtn = true
					this.mainPhoto = this.PhotoData.japanHKD[3]
					this.location = this.LocationData.japanHKD[1]
					this.pageNum +=1
				}
				else if(this.pageNum == 2)
				{
					this.pageNum +=1
					this.nextBtn = false
					this.mainPhoto = this.PhotoData.japanHKD[4]
					this.subPhoto01 = this.PhotoData.japanHKD[5]
					this.location = this.LocationData.japanHKD[2]
				}
			}
			else if(tab == 2)
			{
				if(this.pageNum == 1)
				{
					this.pageNum +=1
					this.backBtn = true
					this.ablBtn = false
					this.mainPhoto = this.PhotoData.japanTHK[2]
					this.subPhoto01 = this.PhotoData.japanTHK[3]
					this.location = this.LocationData.japanTHK[1]
				}
				else if(this.pageNum == 2)
				{
					this.pageNum +=1
					this.mainPhoto = this.PhotoData.japanTHK[4]
					this.subPhoto01 = this.PhotoData.japanTHK[5]
					this.subPhoto02 = this.PhotoData.japanTHK[6]
					this.location = this.LocationData.japanTHK[2]
				}
			}
			else if(tab == 3)
			{
				if(this.pageNum == 1)
				{
					this.pageNum +=1
					this.backBtn = true
					this.ablBtn = false
					this.mainPhoto = this.PhotoData.japanKNT[3]
					this.subPhoto01 = this.PhotoData.japanKNT[4]
					this.subPhoto02 = this.PhotoData.japanKNT[5]
					this.location = this.LocationData.japanKNT[1]
				}
				else if(this.pageNum == 2)
				{
					this.pageNum +=1
					this.mainPhoto = this.PhotoData.japanKNT[6]
					this.subPhoto01 = this.PhotoData.japanKNT[7]
					this.subPhoto02 = this.PhotoData.japanKNT[8]
					this.location = this.LocationData.japanKNT[2]
				}
				else if(this.pageNum == 3)
				{
					this.pageNum +=1
					this.mainPhoto = this.PhotoData.japanKNT[9]
					this.subPhoto01 = this.PhotoData.japanKNT[10]
					this.location = this.LocationData.japanKNT[3]
					this.nextBtn = true
				}
			}
			else if(tab == 4)
			{
				if(this.pageNum == 1)
				{
					this.pageNum +=1
					this.backBtn = true
					this.ablBtn = false
					this.mainPhoto = this.PhotoData.japanKSE[2]
					this.subPhoto01 = this.PhotoData.japanKSE[3]
					this.subPhoto02 = this.PhotoData.japanKSE[4]
					this.location = this.LocationData.japanKSE[1]
				}
			}
			else if(tab == 5)
			{
				if(this.pageNum == 1)
				{
					this.pageNum +=1
					this.backBtn = false
					this.nextBtn = true
					this.mainPhoto = this.PhotoData.japanHKR[2]
					this.subPhoto01 = this.PhotoData.japanHKR[3]
					this.location = this.LocationData.japanHKR[1]
				}
			}
			else if(tab == 6)
			{
				if(this.pageNum == 1)
				{
					this.pageNum +=1
					this.backBtn = false
					this.nextBtn = true
					this.mainPhoto = this.PhotoData.japanTKI[2]
					this.subPhoto01 = this.PhotoData.japanTKI[3]
					this.location = this.LocationData.japanTKI[1]
				}
			}
			else if(tab == 7)
			{
				if(this.pageNum == 1)
				{
					this.pageNum +=1
					this.backBtn = false
					this.nextBtn = true
					this.mainPhoto = this.PhotoData.japanKNK[2]
					this.subPhoto01 = this.PhotoData.japanKNK[3]
					this.subPhoto02 = this.PhotoData.japanKNK[4]
					this.location = this.LocationData.japanKNK[1]
				}else if(this.pageNum == 2)
				{
					this.pageNum +=1
					this.nextBtn = true
					this.mainPhoto = this.PhotoData.japanKNK[5]
					this.subPhoto01 = this.PhotoData.japanKNK[6]
					this.location = this.LocationData.japanKNK[2]
				}
			}
			else if(tab == 8)
			{
				if(this.pageNum == 1)
				{
					this.pageNum +=1
					this.backBtn = false
					this.nextBtn = true
					this.mainPhoto = this.PhotoData.japanCGK[2]
					this.subPhoto01 = this.PhotoData.japanCGK[3]
					this.location = this.LocationData.japanCGK[1]
				}else if(this.pageNum == 2)
				{
					this.pageNum +=1
					this.nextBtn = true
					this.mainPhoto = this.PhotoData.japanCGK[4]
					this.subPhoto01 = this.PhotoData.japanCGK[5]
					this.location = this.LocationData.japanCGK[2]
				}
			}
			else if(tab == 9)
			{
				if(this.pageNum == 1)
				{
					this.pageNum +=1
					this.backBtn = false
					this.nextBtn = true
					this.mainPhoto = this.PhotoData.japanSKK[3]
					this.subPhoto01 = this.PhotoData.japanSKK[4]
					this.subPhoto02 = this.PhotoData.japanSKK[5]
					this.location = this.LocationData.japanSKK[1]
				}
			}
			else if(tab == 10)
			{
				if(this.pageNum == 1)
				{
					this.mainPhoto = this.PhotoData.japanKSY[2]
					this.subPhoto01 = this.PhotoData.japanKSY[3]
					this.subPhoto02 = this.PhotoData.japanKSY[4]
					this.location = this.LocationData.japanKSY[2]
					this.backBtn = false
					this.pageNum +=1
				}else if(this.pageNum == 2)
				{
					this.mainPhoto = this.PhotoData.japanKSY[5]
					this.subPhoto01 = this.PhotoData.japanKSY[6]
					this.subPhoto02 = this.PhotoData.japanKSY[7]
					this.location = this.LocationData.japanKSY[3]
					this.location02 = this.LocationData.japanKSY[4]
					this.location03 = this.LocationData.japanKSY[5]
					this.nextBtn = true
					this.pageNum +=1
				}
			}
		},
		of(){
			this.isShow = false
			this.isNum = 0
			this.popmainPhoto =''
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
	color: rgba(0, 0, 0, 0.719);
}
.el_imgNum_txt_def{
	margin: 0 1%;
  text-align: center;
	padding: 3px;
	color: rgba(59, 59, 59, 0.226);
}
.onCircle {
  width: 20px;
	margin: 0 1%;
	background-color:rgba(0, 0, 0, 0.719);
  border-radius: 50%; 
  text-align: center;
  line-height: 20px;
	padding: 3px;
	color: rgba(255, 255, 255, 0.959);
}
.circle {
  width: 20px;
	margin: 0 1%;
  background-color:rgba(59, 59, 59, 0.226);
	color: rgba(255, 255, 255, 0.959);
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

.el_btn{
	display: inline-block;
}
.bl_pht01_p01_m01{
	position: absolute;
	left: 5%;
	top: 10%;
	width: 30%;
	height: 75%;
	z-index: 1;
}
.bl_pht01_p01_sub01{
	position: absolute;
	left: 45%;
	top: 10%;
	width: 30%;
	height: 30%;
	z-index: 1;
}
.bl_pht01_p01_sub02{
	position: absolute;
	left: 55%;
	top: 50%;
	width: 30%;
	height: 30%;
	z-index: 1;
}

.bl_pht01_p02_m{
	position: absolute;
	left: 15%;
	top: 15%;
	width: 70%;
	height: 75%;
	z-index: 1;
}

.bl_pht01_p03_m{
	position: absolute;
	left: 5%;
	top: 10%;
	width: 40%;
	height: 55%;
	z-index: 1;
}
.bl_pht01_p03_sub01{
	position: absolute;
	left: 55%;
	top: 30%;
	width: 40%;
	height: 55%;
	z-index: 1;
}

.bl_pht02_p01_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht02_p01_sub01{
	position: absolute;
	left: 70%;
	top: 20%;
	width: 20%;
	height: 50%;
	z-index: 1;
}

.bl_pht02_p02_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht02_p02_sub01{
	position: absolute;
	left: 60%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht02_p03_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht02_p03_sub01{
	position: absolute;
	left: 60%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht02_p03_sub02{
	position: absolute;
	left: 60%;
	top: 10%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht03_p01_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht03_p01_sub01{
	position: absolute;
	left: 60%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht03_p01_sub02{
	position: absolute;
	left: 60%;
	top: 10%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht03_p02_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht03_p02_sub01{
	position: absolute;
	left: 60%;
	top: 55%;
	width: 20%;
	height: 40%;
	z-index: 1;
}

.bl_pht03_p02_sub02{
	position: absolute;
	left: 70%;
	top: 5%;
	width: 20%;
	height: 40%;
	z-index: 1;
}

.bl_pht03_p03_m{
	position: absolute;
	left: 5%;
	top: 25%;
	width: 20%;
	height: 70%;
	z-index: 1;
}

.bl_pht03_p03_sub01{
	position: absolute;
	left: 75%;
	top: 15%;
	width: 20%;
	height: 70%;
	z-index: 1;
}

.bl_pht03_p03_sub02{
	position: absolute;
	left: 30%;
	top: 20%;
	width: 40%;
	height: 70%;
	z-index: 1;
}

.bl_pht03_p04_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht03_p04_sub01{
	position: absolute;
	left: 70%;
	top: 20%;
	width: 20%;
	height: 60%;
	z-index: 1;
}

.bl_pht04_p01_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht04_p01_sub01{
	position: absolute;
	left: 60%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht04_p02_m{
	position: absolute;
	left: 75%;
	top: 15%;
	width: 20%;
	height: 70%;
	z-index: 1;
}

.bl_pht04_p02_sub01{
	position: absolute;
	left: 30%;
	top: 20%;
	width: 40%;
	height: 70%;
	z-index: 1;
}

.bl_pht04_p02_sub02{
	position: absolute;
	left: 5%;
	top: 25%;
	width: 20%;
	height: 70%;
	z-index: 1;
}

.bl_pht05_p01_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht05_p01_sub01{
	position: absolute;
	left: 60%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht05_p02_m{
	position: absolute;
	left: 15%;
	top: 20%;
	width: 30%;
	height: 60%;
	z-index: 1;
}

.bl_pht05_p02_sub01{
	position: absolute;
	left: 60%;
	top: 40%;
	width: 20%;
	height: 50%;
	z-index: 1;
}

.bl_pht06_p01_m{
	position: absolute;
	left: 50%;
	top: 20%;
	width: 40%;
	height: 60%;
	z-index: 1;
}

.bl_pht06_p01_sub01{
	position: absolute;
	left: 15%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht06_p02_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 40%;
	height: 55%;
	z-index: 1;
}

.bl_pht06_p02_sub01{
	position: absolute;
	left: 55%;
	top: 40%;
	width: 40%;
	height: 55%;
	z-index: 1;
}

.bl_pht07_p01_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht07_p01_sub01{
	position: absolute;
	left: 70%;
	top: 25%;
	width: 20%;
	height: 60%;
	z-index: 1;
}

.bl_pht07_p02_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht07_p02_sub01{
	position: absolute;
	left: 65%;
	top: 50%;
	width: 20%;
	height: 40%;
	z-index: 1;
}

.bl_pht07_p02_sub02{
	position: absolute;
	left: 75%;
	top: 10%;
	width: 20%;
	height: 40%;
	z-index: 1;
}

.bl_pht07_p03_m{
	position: absolute;
	left: 30%;
	top: 10%;
	width: 20%;
	height: 60%;
	z-index: 1;
}

.bl_pht07_p03_sub01{
	position: absolute;
	left: 60%;
	top: 30%;
	width: 20%;
	height: 60%;
	z-index: 1;
}

.bl_pht08_p01_m{
	position: absolute;
	left: 50%;
	top: 20%;
	width: 40%;
	height: 60%;
	z-index: 1;
}

.bl_pht08_p01_sub01{
	position: absolute;
	left: 15%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht08_p02_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht08_p02_sub01{
	position: absolute;
	left: 60%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht08_p03_m{
	position: absolute;
	left: 50%;
	top: 20%;
	width: 40%;
	height: 60%;
	z-index: 1;
}

.bl_pht08_p03_sub01{
	position: absolute;
	left: 15%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht09_p01_m{
	position: absolute;
	left: 10%;
	top: 20%;
	width: 40%;
	height: 60%;
	z-index: 1;
}

.bl_pht09_p01_sub01{
	position: absolute;
	left: 60%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht09_p01_sub02{
	position: absolute;
	left: 60%;
	top: 10%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht09_p02_m{
	position: absolute;
	left: 50%;
	top: 20%;
	width: 40%;
	height: 60%;
	z-index: 1;
}

.bl_pht09_p02_sub01{
	position: absolute;
	left: 10%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht09_p02_sub02{
	position: absolute;
	left: 10%;
	top: 10%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht010_p01_m{
	position: absolute;
	left: 5%;
	top: 20%;
	width: 50%;
	height: 60%;
	z-index: 1;
}

.bl_pht010_p01_sub01{
	position: absolute;
	left: 60%;
	top: 25%;
	width: 20%;
	height: 60%;
	z-index: 1;
}

.bl_pht010_p02_m{
	position: absolute;
	left: 15%;
	top: 50%;
	width: 30%;
	height: 40%;
	z-index: 1;
}

.bl_pht010_p02_sub01{
	position: absolute;
	left: 50%;
	top: 20%;
	width: 40%;
	height: 60%;
	z-index: 1;
}

.bl_pht010_p03_m{
	position: absolute;
	top: 20%;
	left: 40%;
	width: 20%;
	height: 70%;
	z-index: 1;
	z-index: 1;
}

.bl_pht010_p03_sub01{
	position: absolute;
	left: 65%;
	top: 15%;
	width: 30%;
	height: 70%;
	z-index: 1;
}

.bl_pht010_p03_sub02{
	position: absolute;
	left: 5%;
	top: 25%;
	width: 30%;
	height: 70%;
	z-index: 1;
}


.bl_pht011_p01_m{
	position: absolute;
	left: 65%;
	top: 30%;
	width: 30%;
	height: 60%;
	z-index: 1;
}

.bl_pht011_p01_sub01{
	position: absolute;
	left: 10%;
	top: 15%;
	width: 50%;
	height: 60%;
	z-index: 1;
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

.el_img_ver{
	position: absolute;
	width: 100%;
	left: 0%;
	height: 90%;
	box-shadow:  0 2px 2px 0 rgba(0, 0, 0, 0.29);
  box-shadow: 2px 2px 2px 0 rgba(0, 0, 0, 0.795);
}

.el_pht_txt{
	font-weight: bold;
	position: absolute;
	top       : 45%;
	left      : 50%;
	z-index: -1;
	transform : translate(-50%, -50%);
}

.el_img_ver_js{
	position: absolute;
	width: 100%;
	left: 0%;
	height: 90%;
	filter: blur(2px) opacity(30%);
	box-shadow:  0 2px 2px 0 rgba(0, 0, 0, 0.29);
  box-shadow: 2px 2px 2px 0 rgba(0, 0, 0, 0.795);
}

.bl_imgTxt{
	position: absolute;
	display: flex;
	justify-content: center;
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