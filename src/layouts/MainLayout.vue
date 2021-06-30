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
            :obj="link.obj"
            :title="title"
            v-bind="link"
          />
        </q-list>

      </q-scroll-area>

      <div class="absolute" style="bottom: 15px; left: -17px">
        <q-btn
          dense
          round
          unelevated
          color="primary"
          icon="chevron_left"
          @click="miniState = !miniState"
        ></q-btn>
      </div>
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
    link: '',
    obj: {
      tipo: 'Servicios Digitales y de Información',
      title: 'Servicios Digitales y de Información'
    }
  },
  {
    title: 'Publicaciones digitales',
    caption: 'Revistas, libros y blogs',
    icon: 'poll',
    link: '',
    obj: {
      tipo: 'Publicaciones digitales y Revistas',
      title: 'Publicaciones digitales'
    }
  },
  {
    title: 'Repositorios en línea',
    caption: 'Índices y repositorios',
    icon: 'auto_stories',
    link: '',
    obj: {
      tipo: 'Repositorios en línea',
      title: 'Bibliotecas en línea',
      slidesNoAun: ['img1', 'img2']
    }
  },
  {
    title: 'Cultura Digital',
    caption: 'Cultura UMSNH',
    icon: 'interests',
    link: '',
    obj: {
      tipo: 'Cultura Digital',
      title: 'Cultura Digital'
    }
  },
  {
    title: 'ADINI - UMSNH',
    caption: 'Agenda Digital Nicolaita',
    icon: 'public',
    link: '',
    obj: {
      tipo: 'Agenda Digital Nicolaita - ADINI',
      title: 'ADINI - UMSNH'
    }
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
    //Mini state drawer botón
    const miniState = ref(false)

    return {
      drawer: ref(false),
      miniState,

      drawerClick (e) {
        // if in "mini" state and user
        // click on drawer, we switch it to "normal" mode
        if (miniState.value) {
          miniState.value = false

          // notice we have registered an event with capture flag;
          // we need to stop further propagation as this click is
          // intended for switching drawer to "normal" mode only
          e.stopPropagation()
        }
      }
    }
  }
})
</script>
