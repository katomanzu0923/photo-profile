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
				<div v-if="namState ==2" class="el_err_txt">名前は必ず入力してください。</div>
			</div>
			<div>
				<p class="el_cnta_addr_txt">メールアドレス</p>
				<input type="text" v-model="addr" v-on:change="addrCheck()">
				<div v-if="addrState == 2" class="el_err_txt">＠を含んでメードアドレスを入力してください。</div>
			</div>
			<div>
				<p class="el_cnta_cont_txt">お問い合わせ内容</p>
				<textarea name="text" id="" cols="30" rows="10" v-model="cont" v-on:change="contCheck()" ></textarea>
				<div v-if="contState == 2" class="el_err_txt">質問内容は必ず入力してください。</div>
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
			nameBtn:false,
			addr:'',
			addrBtn:false,
			cont:'',
			contBtn:false,
			namState:1,
			addrState:1,
			contState:1,
			allState:false,
			isBtn:true,
			hu:''
		}
	},
	methods:{
		nameCheck(){
			if(this.name == '')
			{
				this.namState = 2
				this.isBtn = true
			}
			else if(this.name !== '')
			{
				this.namState = 0
				if(this.namState == 0 && this.addrState == 0 && this.contState == 0)
				{
					this.isBtn = false
				}
				else
				{
					this.isBtn = true
				}
			}
		},
		addrCheck(){
			if(this.addr == '' || !this.addr.match(/^([a-zA-Z0-9])+([a-zA-Z0-9_-])*@([a-zA-Z0-9_-])+$/))
			{
				this.addrState = 2
				this.isBtn = true
			}
			else if(this.addr !== '' && this.addr.match(/^([a-zA-Z0-9])+([a-zA-Z0-9_-])*@([a-zA-Z0-9_-])+$/))
			{
				this.addrState = 0
				if(this.namState == 0 && this.addrState == 0 && this.contState == 0)
				{
					this.isBtn =false
				}
				else
				{
					this.isBtn = true
				}
			}
		},
		contCheck(){
			if(this.cont == '')
			{
				this.contState = 2
				this.isBtn = true
			}
			else if(this.cont !== '')
			{
				this.contState = 0
				if(this.namState == 0 && this.addrState == 0 && this.contState == 0)
				{
					this.isBtn =false
				}
				else
				{
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
			this.chkState == false		}
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
	@include media(m){
		font-size: 0.8rem;
	}
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
	margin: 2.5% 0 0;
	padding: 5px;
	border: solid white 1px;
	box-shadow:  0 2px 2px 0 rgba(0, 0, 0, 0.29);
	font-size: 1.5rem;
	@include media(m){
		font-size: 1rem;
	}
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

.el_cnta_nam_txt{
	margin: 10% 5% 0;
}

.el_cnta_addr_txt{
	margin: 10% 5% 0;
}

.el_cnta_cont_txt{
	margin: 10% 0 0;
}

.el_err_txt{
	color: rgba(255, 0, 0, 0.767);
	padding: 2% 0;
}

</style>

