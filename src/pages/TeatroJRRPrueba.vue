<template>
  <q-page class="flex flex-center">
    <div class="main fixed-top" style="width:100%; height:100vh;">

      <TeatroJRR/>

    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import TeatroJRR from 'components/TeatroJRR.vue'

export default defineComponent({
  name: 'Teatro JRR prueba',

  components: {
    TeatroJRR
  }
})
</script>
