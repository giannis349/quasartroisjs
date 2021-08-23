<template>
  <div>
  <p>Ddd</p>
<Espacio3D />
  </div>
</template>

<script>
import Espacio3D from 'components/espacio3D.vue'

export default {
  name: 'HelloWorld',
    components: {
    espacio3D
  },
  props: {
    msg: String
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
