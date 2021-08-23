<template>
  <div id="app">
    <vue-splash
    :show="showSplash"
    :logo="'https://upload.wikimedia.org/wikipedia/commons/1/14/Logo_de_la_UMSNH.svg'"
    title="Campus Digital UMSNH"
    :color="'#ffa900'"
    :size="300"
    :fixed="true"
  />

    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Vue from 'vue';
import VueSplash from 'vue-splash';
import Buefy from 'buefy'
import 'buefy/dist/buefy.css'


Vue.use(VueSplash);
Vue.use(Buefy)

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      showSplash: true
    }
  },
  mounted() {
    setTimeout(() => {
      this.showSplash = false
    }, 1800)
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
