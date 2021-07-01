<template>
  <q-page class="flex flex-center">
    <div class="main fixed-top">

      <q-card class="fixed-center text-center text-white bg-transparent no-border-radius no-border no-shadow"
              style="text-shadow: #1D1D1D 0 0 5px;">
        <q-card-section class="text-weight-bold">
          <h3>Campus digital</h3>
          <h5>
            de la Universidad Michoacana
            <br>
            de San Nicolás de Hidalgo
          </h5>
        </q-card-section>

        <q-card-section>
          <p class="text-h6">
            <strong>La UMSNH más cerca de ti</strong>, En este espacio encontrarás un repositorio
            <br>
            de los servicios que la Casa de Hidalgo oferta en formato digital.
          </p>
        </q-card-section>

      </q-card>

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
