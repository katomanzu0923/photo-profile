
<template>
	<div class="ly">
		<div class="bl_MyProfile">
			<div class="bl_MyProfile_txt">
				<h1 class="el_MyProfile_ttl el_MyProfile_ttl_clr">About  Me</h1>
				<p class="el_MyProfile_cont">名前:加藤貴大</p>
				<p class="el_MyProfile_cont">一言:趣味で写真撮っています</p>
				<p class="el_MyProfile_cont">カメラ歴:9年</p>
				<p class="el_MyProfile_cont">使用カメラ:富士フィルム</p>
			</div>
			<img  class="el_MyProfile_img" :src="imgPath"> 
		</div>
	</div>
</template>



<script>
export default {
	data() {
		return {
			imgPath: require('@/assets/main01.png'),
			photo:require('@/assets/portWORKm.png'),
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
	width: 50%;
	left: 25%;
	height: 100%;
	top: 0%;
}

.bl_MyProfile_txt{
	position: absolute;
	left: 10%;
	top: 5%;
	z-index: 2;
}

.el_MyProfile_ttl{
	border-bottom: navy 2px solid;
	z-index: 1;
}
.el_MyProfile_ttl_clr{
	color: navy;
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
.el_MyProfile_cont{
	text-align: start;
	margin: 2% 5%;
}

</style>