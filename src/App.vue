<template>
  <div id="app">
    <transition name="fade">
      <Popup v-if="isPop" v-on:cha="changepop()"></Popup>
    </transition>
    <Header
      class="revise"
      v-on:change="ChangeMyProfile()"
      v-on:change01="ChangeMybest()"
      v-on:change02="ChangePort()"
      v-on:change03="ChangeStb()"
      v-on:change04="ChangeJp()">
    </Header>
      <MyProfile v-if="tab==0"></MyProfile>
      <Portraito v-if="tab==1"></Portraito>
      <Starbacks v-if="tab==2"></Starbacks>
      <Japan v-if="tab==3"></Japan>
      <MyBests v-if="tab==4"></MyBests>
  </div>
</template>

<script>
import Popup from './components/Popup.vue'
import Header from './components/Header.vue'
import Portraito from './components/Portraito.vue'
import Starbacks from './components/Starbacks.vue'
import Japan from './components/Japan.vue'
import MyProfile from './components/MyProfile.vue'
import MyBests from './components/MyBests.vue'
import 'normalize.css'

export default {
  name: 'App',
  data(){
    return{
      isPop:false,
      tab:0
    }
  },
  components: {
    Popup,
    Header,
    Portraito,
    Starbacks,
    Japan,
    MyProfile,
    MyBests
	},
	computed: {

	},
  methods: {
    changepop() {
      this.isPop = false
    },
    ChangeMybest(){
      this.tab = 1
    },
    ChangeMyProfile() {
      this.tab = 0
    },
    ChangePort() {
      this.tab = 2
    },
    ChangeStb() {
      this.tab = 3
    },
    ChangeJp() {
      this.tab = 4
    }
  }
}
</script>

<style>
.fade-leave-active {
  transition: all 2s ease;
}
.fade-leave{
  opacity: 1;
}
.fade-leave-to {
	opacity: 0;
}
#app {
}
</style>
