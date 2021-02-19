<template>
	<div class="ly_cnta">
		<div class="bl_popCnta" v-show="isPop">
			<div class="bl_popCnta"> 
				<h1 class="bl_popCnta_ttl">
					<span class="el_popCnta_ttl_nam">{{name}}様</span><br>お問い合わせいただきありがとうございます
				</h1>
				<p class="el_popCnta_cont">{{cont}}</p>
				<p>
					といった内容で確かに承りしました。<br>また、ご返事に関しては２、3日いないで返信しますのでしばらくお待ちください
				</p>
			</div>
		</div>
		<div class="bl_cnta">
			<div>
				<h1 class="el_cnta_ttl">お問い合わせフォーム</h1>
			</div>
			<div>
				<p class="el_cnta_nam_txt">お名前</p>
				<input type="text" v-model="name" v-on:change="nameCheck()">
			</div>
			<div>
				<p class="el_cnta_addr_txt">メールアドレス</p>
				<input type="text" v-model="addr" v-on:change="addrCheck()">
			</div>
			<div>
				<p class="el_cnta_cont_txt">お問い合わせ内容</p>
				<textarea name="text" id="" cols="30" rows="10" v-model="cont" v-on:change="contCheck()" ></textarea>
			</div>
			<div>
				<button @click="submit" :class="[isBtn? 'el_cnta_btn': 'el_cnta_btn_js']" :disabled="isBtn" >送信</button>
			</div>
		</div>

	</div>
</template>

<script>
export default {
	data() {
		return {
			ion:'',
			isPop:false,
			name:'',
			addr:'',
			cont:'',
			chkNum:0,
			isBtn:true,
			hu:''
		}
	},
	methods:{
		nameCheck(){
			if(this.name == '')
			{
				if(this.chkNum <= 3)
				{
					this.isBtn = true
					this.chkNum -=1
				}
			}
			else if(this.name !== '')
			{
				if(this.chkNum == 2)
				{
					this.chkNum +=1
					this.isBtn = false
				}
				else if(this.chkNum < 2)
				{
					this.chkNum +=1
					this.isBtn = true
				}
			}
		},
		addrCheck(){
			if(this.addr == '')
			{
				if(this.chkNum <= 3)
				{
					this.isBtn = true
					this.chkNum -=1
				}
			}
			else if(this.addr !== '')
			{
				if(this.chkNum == 2)
				{
					this.chkNum +=1
					this.isBtn = false
				}
				else if(this.chkNum <2)
				{
					this.isBtn = true
					this.chkNum +=1
				}
			}
		},
		contCheck(){
			if(this.cont == '')
			{
				if(this.chkNum <= 3)
				{
					this.isBtn = true
					this.chkNum -=1
				}
			}
			else if(this.cont !== '')
			{
				if(this.chkNum == 2)
				{
					this.chkNum +=1
					this.isBtn = false
				}
				else if(this.chkNum < 2)
				{
					this.chkNum +=1
					this.isBtn = true
				}
			}
		},
		submit(){
			this.isPop = true
			setTimeout(this.auteOut, 5000,);
		},
		auteOut(){
			this.isPop = false
			this.name = ''
			this.addr = ''
			this.cont = ''
			this.chkNum = 0
		}
	}
}
</script>

<style lang="scss" scoped>
input{
	outline: none;
	box-shadow:  0 2px 2px 0 rgba(0, 0, 0, 0.29);
	padding: 2%;
}

textarea{
	outline: none;
	box-shadow:  0 2px 2px 0 rgba(0, 0, 0, 0.29);
	padding: 2%;
}


.ly_cnta {
	position: absolute;
	width: 98%;
	left: 1%;
	top: 10%;
	height: 85%;
	background: rgba(236, 235, 235, 0.856);
	border-left: rgb(206, 206, 221) 2px solid;
}

.bl_popCnta{
}

.bl_popCnta{
	position: absolute;
	z-index: 12;
	width: 101%;
	left: -1%;
	top: -5%;
	height: 112%;
	background: white;
	text-align: center;
}
.bl_popCnta_ttl{
	margin: 2.5% 0;
}

.el_popCnta_ttl_nam{
	display: block;
	font-size: 3rem;
	margin: 1% 0;
}

.el_popCnta_cont{
	margin: 0 10%;
	width: 80%;
	padding: 2%;
	border: 1px solid black;
	text-align: start;
}

.bl_cnta{
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
	text-align: center;
}

.el_cnta_ttl{
	margin: 2.5% 0;
	padding: 5px;
	border: solid white 1px;
	box-shadow:  0 2px 2px 0 rgba(0, 0, 0, 0.29);

}

.el_cnta_btn{
	margin: 20% 0;
	padding: 10px;
}

.el_cnta_btn_js{
	margin: 20% 0;
	padding: 10px;
	background: black;
	color:white;
	box-shadow:  0 2px 2px 0 rgba(0, 0, 0, 0.29);
}

</style>

