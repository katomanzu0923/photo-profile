<template>
	<div class="ly_MyProfile">
		<div class="bl_MyProfile">
			<div class="bl_MyProfile_l">
				<img  class="el_MyProfile_l" :src="imgPath">
			</div>
			<div class="bl_MyProfile_r">
				<h1>ー  MyProfile  ー</h1>
				<p>趣味で写真取ってます。<br>フジフィルムを愛してます。カメラ歴9年</p>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			imgPath: require('@/assets/myprofile01.png')
		}
	}
}
</script>

<style lang="scss" scoped>
  
  .bl_MyProfile {
		margin: 10%;
		justify-content: center;
	}
	.ly_MyProfile{
		position: absolute;
		top: 30%;
		margin-top: 300px;
	}
  .bl_MyProfile_l {
	}
	.bl_MyProfile_l::after {
		position: absolute;
		content: '';
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		box-shadow:inset 0 0 15px 15px white;
	}
	.el_MyProfile_l {
		height: 100px;
		width: 100%;
	}
	.bl_MyProfile_l::after {
  position: absolute;
  content: '';
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  box-shadow:inset 0 0 15px 15px white;
}
	.bl_MyProfile_r {
		position: absolute;
		left: 0;
		top: 100px;
		text-align: center;
		width: 30%;
		background: rgba(192, 192, 192, 0.26);
	}
</style>