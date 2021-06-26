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

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer reveal class="bg-transparent text-white">
      <q-toolbar>
        <q-avatar>
          <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
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

const linksList = [
  {
    title: 'Estudios',
    caption: 'quasar.dev',
    icon: 'school',
    link: '#'
  },
  {
    title: 'Infraestructura',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: '#'
  },
  {
    title: 'Publicaciones',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: '#'
  },
  {
    title: 'Desarrollo',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: '#'
  },
  {
    title: 'Links de prueba 1 ',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: '#'
  },
  {
    title: 'Links de prueba 2 ',
    caption: '@QuasarFramework',
    icon: 'public',
    link: '#'
  },
  {
    title: 'Links de prueba 3',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: '#'
  }
]

import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
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
