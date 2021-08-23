<template>
  <div class="hello">
    <vue-splash
    :show="showSplash"
    :logo="'https://upload.wikimedia.org/wikipedia/commons/1/14/Logo_de_la_UMSNH.svg'"
    title="Campus Digital UMSNH"
    :color="'#ffa900'"
    :size="300"
    :fixed="true"
  />
    <h1>meh</h1>

  </div>
</template>

<script>
import Vue from 'vue';
import VueSplash from 'vue-splash';
import Buefy from 'buefy'
import 'buefy/dist/buefy.css'

Vue.use(VueSplash);
Vue.use(Buefy)

export default {
  name: 'HelloWorld',
  props: {
    msg: String
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
