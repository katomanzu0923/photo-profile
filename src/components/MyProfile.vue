
<template>
	<div class="ly">
		<div class="bl_MyProfile_txt">
			<h1 class="el_MyProfile_ttl el_MyProfile_ttl_clr">About  Me</h1>
			<p class="el_MyProfile_nameCont">兄の影響を受け。写真撮影が趣味に。<br>撮影対象は日本の風景やStarbucks。ポートレイトが苦手なため現在練習中。
			</p>
			<p class="el_MyProfile_cont">好きな機材は富士フィルム・35mmF1.4がレンズの中では１番のお気に入り。</p>
		</div>
		<div class="bl_MyProfile">
			<img  class="el_MyProfile_img" :src="imgPath"> 
		</div>
	</div>
</template>



<script>
export default {
	data() {
		return {
			imgPath: require('@/assets/main01.png'),
		}
	},
	methods:{
		os(){
			alert('a')
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


.bl_MyProfile{
	position: absolute;
	width: 30%;
	left: 70%;
	height: 100%;
	top: 0%;
}

.bl_MyProfile_txt{
	position: absolute;
	display: flex;
	justify-content: center;
	flex-direction: column;
	left: 0%;
	top: 0;
	z-index: 2;
	width: 70%;
	text-align: start;
}

.el_MyProfile_ttl{
	border-bottom: navy 2px solid;
	z-index: 1;
	padding: 0 2%;
}
.el_MyProfile_ttl_clr{
	color: black;
}
.el_MyProfile_img{
	position: absolute;
	width: 90%;
	height: 90%;
	left: 5%;
	z-index: 0;
	top: 5%;
	box-shadow: 3px 3px 0px 0 rgba(0, 0, 0, 0.548);
	filter: opacity(100%);
}
.el_MyProfile_nameTtl{
	margin: 0 0;
}
.el_MyProfile_nameCont{
	margin:  1% 10%;
	padding: 5px 5px;
	width: 80%;
}

</style>