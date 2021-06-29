<template>
  <q-layout view="lHr LpR ffr">
    <q-header class="col-auto bg-transparent" style="left: unset;">
      <q-toolbar class="col-auto bg-blue-5">
        <q-title >Campus Digital UMSNH</q-title>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="rightDrawerOpen"
      show-if-above

      :mini="miniState"
      @mouseover="miniState = false"
      @mouseout="miniState = true"

      :width="300"
      :breakpoint="600"

      side="right"
      behavior="desktop"
      bordered
      class="bg-grey-1 row"
    >
      <q-scroll-area class="fit">
        <q-list>
          <EssentialLink
            v-for="link in essentialLinks"
            :key="link.title"
            v-bind="link"
          />
        </q-list>

      </q-scroll-area>
    </q-drawer>

    <Dialog/>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer reveal class="bg-transparent text-white">
      <q-toolbar>
        <q-avatar>
          <img src="~assets/umsnh_escudo_svg_v1.svg">
        </q-avatar>
        <q-text text-overline class="text-white q-px-sm">
          <span>
            Universidad Michoacana de San nicolas de Hidalgo
          </span>
        </q-text>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'
import Dialog from 'components/Dialog.vue'

const linksList = [
  {
    title: 'Campus Digital',
    caption: 'UMSNH',
    icon: 'home',
    link: './'
  },
  {
    title: 'Plataformas de Educación',
    caption: 'UMSNH',
    icon: 'school',
    link: './teatro-jrr-prueba'
  },
  {
    title: 'Servicios Digitales y de Información',
    caption: 'y de Información',
    icon: 'record_voice_over',
    link: ''
  },
  {
    title: 'Publicaciones digitales',
    caption: 'Revistas, libros y blogs',
    icon: 'poll',
    link: ''
  },
  {
    title: 'Bibliotecas en línea',
    caption: 'Índices y repositorios',
    icon: 'auto_stories',
    link: ''
  },
  {
    title: 'Cultura Digital',
    caption: 'Cultura UMSNH',
    icon: 'interests',
    link: ''
  },
  {
    title: 'ADINI - UMSNH',
    caption: 'Agenda Digital Nicolaita',
    icon: 'public',
    link: ''
  }
]

import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink,
    Dialog
  },

  setup () {
    const rightDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      rightDrawerOpen,
      toggleLeftDrawer () {
        rightDrawerOpen.value = !rightDrawerOpen.value
      },
      miniState: ref(true)
    }
  }
})
</script>
