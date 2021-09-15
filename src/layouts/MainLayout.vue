<template>
  <div class="q-pa-md q-gutter-y-sm">

  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          GUNDAM-DEMO Sガンダム
        </q-toolbar-title>

        <div>ガンダム
</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>

       <q-card class="my-card bg-negative
 text-white">
      <q-card-section>
<q-btn round>
     <img
      alt="Quasar logo"
      src="~assets/250px-Gundam.jpg"
      style="width: 200px; height: 200px; border-radius: 100px;"
    >
          </q-btn>
         <q-chip>
        <q-avatar>
          <img src="https://cdn.quasar.dev/img/boy-avatar.png">
        </q-avatar>
        John
      </q-chip>

        <div class="text-h6"> GUNDAM-DEMO Sガンダム</div>
        <div class="text-subtitle2">let's enjoy</div>
      </q-card-section>

    </q-card>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
  </div>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: '00 GUNDAM',
    caption: 'aka GN-0000, 00 Gundam, 00, pronounced "Double-Oh"',
    icon: 'build',
    link: 'pages/CHERUDIM.vue'
  },
  {
    title: '00 RAISER',
    caption: 'aka GN-0000 00 Gundam and GNR-010 0 Raiser',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'CHERUDIM GUNDAM',
    caption: 'aka Cherudim Gundam, Cherudim',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'GUNDAM KYRIOS',
    caption: 'aka Gundam Kyrios, Kyrios',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'TIEREN GROUND',
    caption: 'aka Tieren Ground Type, Tieren',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'สมาชิกในกลุ่ม',
    caption: 'Members in project',
    icon: 'people',
    link: 'https://awesome.quasar.dev'
  }
]

import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
