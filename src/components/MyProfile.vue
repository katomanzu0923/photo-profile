
<template>
	<div class="ly">
		<div class="bl_btn">
				<p :class="[tabCheck== 0? 'el_img_ttl':'el_img_ttl_def' ]"  @click="changeTab(0)">北海道・東北</p>
			</div>
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
					<img class="el_MyProfile_img01" :src="photo" @click="os()">
			</div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			tabCheck:0,
			tabState:0,
			NumM:'',
			Numl:'',
			Numr:'',
			secNum:0,
			check:0,
			check01:0,
			check02:0,
			check03:0,
			isPart:0,
			isNum:0,
			isShow:false,
			popphoto:'',
		}
	},
	mounted:{
		ui(){
			this.photo = this.PhotoData.portWORK[0]
		}
	},
	methods:{
		karis(){
			alert('a')
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

</style>
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
.ly_MyProfile{
	position: relative;
	width: 100%;
	height: 90%;
	margin-top: 7%;
}
.bl_MyProfile{
	position: absolute;
	width: 40%;
	left: 30%;
	top: 5%;
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
	width: 100%;
	height: 750px;
	top: -5%;
	box-shadow: 3px 3px 0px 0 rgba(0, 0, 0, 0.548);
	transform:rotate(0deg); 
		filter: opacity(100%);
}
.el_MyProfile_img01{
	position: absolute;
	left: 1%;
	width: 100%;
	height: 750px;
	z-index: -1;
	top: 1%;
	box-shadow: 3px 3px 0px 0 rgba(0, 0, 0, 0.548);
	filter: opacity(100%);
}
.el_MyProfile_cont{
	text-align: start;
	margin: 2% 5%;
}
.bl_img{
	position: absolute;
	width: 100%;
	height: 70vh;
	z-index: -5;
}

.el_popImg02{
	position: absolute;
	width: 25%;
	height: 60%;
	right: 0%;
	top: -10%;
	transform:rotate(4deg); 
	filter: opacity(50%);
}
.el_popImg03{
	position: absolute;
	width: 20%;
	height: 30%;
	right: 0%;
	top: 40%;
	transform:rotate(-15deg); 
	border: 3px solid navy;
	box-shadow:0 5px 5px rgba(0, 0, 0, 0.685);
	filter: opacity(50%);
}
.el_popImg04{
	position: absolute;
	width: 20%;
	height: 40%;
	right: 0%;
	top: 75%;
	z-index: -1;
	border: 3px solid navy;
	transform:rotate(-1deg); 
	box-shadow:0 10px 2.5px rgba(0, 0, 0, 0.057);
	filter: opacity(50%);
}
.el_popImg05{
	position: absolute;
	width: 20%;
	height: 40%;
	right: 40%;
	top: -25%;
	z-index: -1;
	border: 3px solid navy;
	transform:rotate(-1deg); 
	box-shadow:0 10px 2.5px rgba(0, 0, 0, 0.057);
}
.el_popImg06{
	position: absolute;
	width: 20%;
	height: 40%;
	right: 30%;
	top: 25%;
	z-index: -1;
	border: 3px solid navy;
	transform:rotate(-1deg); 
	box-shadow:0 10px 2.5px rgba(0, 0, 0, 0.057);
}
.el_popImg07{
	position: absolute;
	width: 20%;
	height: 40%;
	right: 30%;
	top: 75%;
	z-index: -1;
	border: 3px solid navy;
	transform:rotate(-1deg); 
	box-shadow:0 10px 2.5px rgba(0, 0, 0, 0.057);
}
.el_popImg08{
	position: absolute;
	width: 30%;
	height: 20%;
	left: 2%;
	top: 0%;
	z-index: -1;
	border: 3px solid navy;
	transform:rotate(4deg); 
	box-shadow:0 10px 2.5px rgba(0, 0, 0, 0.057);
	filter: opacity(50%);
}
.el_popImg09{
	position: absolute;
	width: 20%;
	height: 25%;
	left: 3%;
	top: 35%;
	z-index: -1;
	border: 3px solid navy;
	transform:rotate(-5deg); 
	box-shadow:0 10px 2.5px rgba(0, 0, 0, 0.057);
	filter: opacity(50%);
}
.el_popImg010{
	position: absolute;
	width: 20%;
	height: 40%;
	left: 5%;
	top: 80%;
	z-index: -1;
	border: 3px solid navy;
	transform:rotate(-1deg); 
	box-shadow:0 10px 2.5px rgba(0, 0, 0, 0.057);
	filter: opacity(50%);
}
</style>