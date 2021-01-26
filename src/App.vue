<template>
  <div id="app">
    <transition name="fade">
      <Popup v-if="hu" v-on:cha="changepop()"></Popup>
    </transition>
    <Header 
      v-on:change="ChangePort()"
      v-on:change02="ChangeStb()"
      v-on:change03="ChangeJp()">
    </Header>
      <Portraito v-if="tab==0"></Portraito>
      <Starbacks v-if="tab==1">s</Starbacks>
      <Japan v-if="tab==2"></Japan>
      <Portraito v-if="tab==3"></Portraito>
      <Portraito v-if="tab==4"></Portraito>
  </div>
</template>

<script>
import Popup from './components/Popup.vue'
import Header from './components/Header.vue'
import Portraito from './components/Portraito.vue'
import Starbacks from './components/Starbacks.vue'
import Japan from './components/Japan.vue'

export default {
  name: 'App',
  data(){
    return{
      hu:true,
      a:'f',
      tab:0
    }
  },
  components: {
    Popup,
    Header,
    Portraito,
    Starbacks,
    Japan
  },
  methods: {
    changepop() {
      this.hu = false
    },
    ChangePort() {
      this.tab = 0
    },
    ChangeStb() {
      this.tab = 1
    },
    ChangeJp() {
      this.tab = 2
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
