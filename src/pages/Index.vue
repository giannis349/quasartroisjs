<template>
  <q-page class="flex flex-center">
    <div class="main fixed-top" style="width:100%; height:100vh;">

      <Espacio3D/>

    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import Espacio3D from 'components/Espacio3D.vue'

export default defineComponent({
  name: 'PageIndex',

  components: {
    Espacio3D
  }
})
</script>
