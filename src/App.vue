<template>
  <div id="app">
    <transition name="fade">
      <Popup v-if="isPop" v-on:cha="changepop()"></Popup>
    </transition>
    <Header 
      v-on:change="ChangeMyProfile()"
      v-on:change1="ChangePort()"
      v-on:change02="ChangeStb()"
      v-on:change03="ChangeJp()">
    </Header>
      <MyProfile v-if="tab==0"></MyProfile>
      <Portraito v-if="tab==1"></Portraito>
      <Starbacks v-if="tab==2">s</Starbacks>
      <Japan v-if="tab==3"></Japan>
  </div>
</template>

<script>
import Popup from './components/Popup.vue'
import Header from './components/Header.vue'
import Portraito from './components/Portraito.vue'
import Starbacks from './components/Starbacks.vue'
import Japan from './components/Japan.vue'
import MyProfile from './components/MyProfile.vue'
import 'normalize.css'

export default {
  name: 'App',
  data(){
    return{
      isPop:true,
      tab:0
    }
  },
  components: {
    Popup,
    Header,
    Portraito,
    Starbacks,
    Japan,
    MyProfile
  },
  methods: {
    changepop() {
      this.isPop = false
    },
    ChangeMyProfile() {
      this.tab = 0
    },
    ChangePort() {
      this.tab = 1
    },
    ChangeStb() {
      this.tab = 2
    },
    ChangeJp() {
      this.tab = 3
    }
  }
}
</script>

<style>
.fade-leave-active {
  transition: all 3s ease;
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
