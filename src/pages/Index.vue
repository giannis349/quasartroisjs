<template>
  <q-page class="flex flex-center">
    <vue-splash
    :show="true"
    :logo="'https://mehdikhoshnevisz.github.io/vue-splash/img/vue.f4b57650.svg'"
    title="Your Magnificent App Name"
    color="#00bfa5"
    :size="300"
    :fixed="true"
  />
    <div class="main fixed-top">

      <q-card class="fixed-center text-center text-white bg-transparent no-border-radius no-border no-shadow"
              style="text-shadow: #1D1D1D 0 0 5px;">
        <q-card-section>
          <img src="~assets/logopng.png" alt="Escudo UMSNH">
          <h3 class="q-mt-sm q-mb-md text-weight-bold">Campus Digital</h3>
          <h5 class="q-my-sm text-weight-light">
            Universidad Michoacana
            <br>
            de San Nicolás de Hidalgo
          </h5>
        </q-card-section>

        <q-card-section>
          <p class="text-h6 text-white text-weight-light">
            <strong>La Universidad más cerca de ti</strong>. En este espacio encontrarás un repositorio de los servicios que la Casa de Hidalgo oferta en formato digital.
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
import Vue from 'vue';
import VueSplash from 'vue-splash';

Vue.use(VueSplash);

export default defineComponent({
  name: 'PageIndex',

  components: {
    Espacio3D
  }
})
</script>
