<template>
	<div class="ly_MyProfile">
			<div class="bl_MyProfile">
				<div class="l">
					<h1 class="el_MyProfile_ttl el_MyProfile_ttl_clr">About  Me</h1>
					<p class="el_MyProfile_cont">名前:加藤貴大</p>
					<p class="el_MyProfile_cont">一言:趣味で写真撮っています</p>
					<p class="el_MyProfile_cont">カメラ歴:9年</p>
					<p class="el_MyProfile_cont">使用カメラ:富士フィルム</p>
				</div>
				<div class="r">
					<img  class="el_MyProfile_img" :src="imgPath">
				</div>
			</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			imgPath: require('@/assets/main01.png')
		}
	}
}
</script>

<style lang="scss" scoped>
.ly_MyProfile{
	z-index: -1;
	position: relative;
	width: 60%;
	margin: 2% 20%;
}
.bl_MyProfile{
	display: flex;
	justify-content: space-around;
}
.l{
	position: absolute;
	width: 30%;
	left: 5%;
	z-index: 1;
}
.el_MyProfile_ttl{
	border-bottom: navy 2px solid;
}
.el_MyProfile_ttl_clr{
	color: navy;
}
.el_MyProfile_img{
	position: absolute;
	right: 0;
	width: 100%;
	height: 750px;
	border: navy 2px solid;
	filter: opacity(80%);
}
.el_MyProfile_cont{
	text-align: start;
	margin: 2% 5%;
}
</style>