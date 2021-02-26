
<template>
	<div class="ly">
		<h1 class="el_MyProfile_ttl el_MyProfile_ttl_clr">About  Me</h1>
		<div class="bl_MyProfile_txt">
			<div class="bl_MyProfile_txt_cont">
				<p class="el_MyProfile_nameCont">Profile</p>
				<p class="el_MyProfile_txt_cont">氏名 ： 加藤貴大  居住地 : 東京都</p>
				<p class="el_MyProfile_txt_cont">兄の影響を受け学生時代から趣味が写真撮影に。好きな機材はFUJIFILM。</p>
				<p class="el_MyProfile_nameCont">Strong Skill</p>
				<p class="el_MyProfile_txt_cont">Portraito 風景 カフェ</p>
				<p class="el_MyProfile_nameCont">My Site</p>
				<p class="el_MyProfile_txt_cont">
					<img :src="instagramPath" :class="[popState01? 'el_popImg': 'el_popImg_def']" v-on:mouseover="u(1)" v-on:mouseleave="out(1)">
					<img :src="twitterPath" :class="[popState02? 'el_popImg': 'el_popImg_def']" v-on:mouseover="u(2)" v-on:mouseleave="out(2)">
				</p>
			</div>
		</div>
		<div class="bl_MyProfile_img">
			<img  class="el_MyProfile_img" :src="imgPath"> 
		</div>
	</div>
</template>



<script>
export default {
	data() {
		return {
			imgPath: require('@/assets/main01.png'),
			instagramPath: require('@/assets/instagram.png'),
			twitterPath: require('@/assets/twitter.png'),
			popState01:false,
			popState02:false,
			instName:'Instgram',
			twiName:'Twitter'
		}
	},
	methods:{
		os(){
			alert('a')
		},
		u(Num){
			if(Num == 1){
				this.popState01 = true
				this.instName = '準備中'
				this.popState02 = false
			}
			else if(Num == 2)
			{
				this.popState01 = false
				this.twiName = '準備中'
				this.popState02 = true
			}
		},
		out(){
				this.popState01 = false
				this.popState02 = false
				this.instName = 'Instagram'
				this.twiName = 'Twitter'
		

		}

	}
}
</script>

<style lang="scss" scoped>
$breakpoints: (
	m: "only screen and (max-width: 980px)",
	pc: "only screen and (max-width: 1199px)",
);
@mixin media($breakpoint) {
	@media #{map-get($breakpoints, $breakpoint)} {
		@content;
	}
}
.ly {
	position: absolute;
	width: 98%;
	left: 1%;
	top: 10%;
	height: 85%;
	background: rgba(236, 235, 235, 0.856);
	border-left: rgb(206, 206, 221) 2px solid;
	@include media(m){
		font-size: 0.8rem;
	}
}


.bl_MyProfile_img{
	position: absolute;
	width: 50%;
	left: 45%;
	height: 80%;
	top: 10%;
	@include media(m){
		position: none;
		width: 80%;
		height: 50%;
		left: 10%;
		top: 5%;
	}
}

.bl_MyProfile_txt{
	position: absolute;
	display: flex;
	justify-content: center;
	flex-direction: column;
	left: 0%;
	top: 5%;
	z-index: 2;
	width: 50%;
	height: 100%;
	text-align: start;
	@include media(m){
		top: 55%;
		width: 90%;
		left: 5%;
		height: 40%;
	}
}

.el_MyProfile_ttl{
	border-bottom: rgba(0, 0, 0, 0.425) 2px solid;
	z-index: 1;
	width: 60%;
	margin-left: 5%;
	margin-top: 2%;
	@include media(m){
		position: absolute;
		top: 2%;
		left: 10%;
		margin: 0;
		width: 80%;
		font-size: 1rem;
	}
}

.el_MyProfile_nameCont{
	border-bottom: 0.5px solid rgba(0, 0, 0, 0.425);
	width: 80%;
	margin-left: 10%;
	font-weight: bold;
}

.el_MyProfile_txt_cont{
	width: 80%;
	margin-left: 12.5%;
	
}

.bl_MyProfile_txt_cont{
	margin-left: 10%;
	width: 80%;
	height: 80%;
	@include media(m){
		position: absolute;
		margin: 0;
		height: 100%;
		left: 10%;
	}
}

.el_MyProfile_img{
	position: absolute;
	width: 80%;
	height: 90%;
	top: 5%;
	left: 10%;
	z-index: 0;
	box-shadow: 3px 3px 0px 0 rgba(0, 0, 0, 0.548);
	filter: opacity(100%);
	@include media(m){
		width: 80%;
	}
}
.el_MyProfile_nameTtl{
	margin: 0 0;
}

.el_popImg_def {
	margin: 0 2%;
	width: 5%;
	height: 5%;
}
.el_popImg{
	margin: 0 2%;
	width: 5%;
	height: 5%;
	filter: opacity(30%);
}

.el_MyProfile_nameCont{
}

.kari01{
	position: absolute;
	font-size: 0.5rem;
	left: 25%;
	top: 52%;
	background-image: url("~@/assets/twitter.png");
}

.kari02{
	position: absolute;
	left: 31%;
	top: 52%;
	background-image: url("~@/assets/twitter.png");
}

</style>