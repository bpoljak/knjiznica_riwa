<template>
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

        <q-toolbar-title class="text-h3">
          Knjižnica
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Essential Links
        </q-item-label>

        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

defineOptions({
  name: 'MainLayout'
})

const linksList = [
  {
    title: 'Početna',
    caption: 'Početna stranica',
    icon: 'home',
    link: '/'
  },
  {
    title: 'Popis knjiga',
    caption: 'Popis svih kniga u knjižnici',
    icon: 'book',
    link: '/popisKnjiga'
  },
  {
    title: 'Pretraživanje',
    caption: 'Pretraživanje knjiga po imenu',
    icon: 'search',
    link: '/pretrazivanje'
  },
  {
    title: 'O nama',
    caption: 'Informacije o knjižnici',
    icon: 'record_voice_over',
    link: '/o_nama'
  },
  {
    title: 'Lokacija',
    caption: 'Informacije o lokaciji knjižnice',
    icon: 'location',
    link: '/lokacija'
  },
  {
    title: 'Prijava',
    caption: 'Prijavite se u svoj korisnički račun',
    icon: 'login',
    link: '/login'
  },
  {
    title: 'Registracija',
    caption: 'Kreirajte svoj korisnički račun',
    icon: 'register',
    link: '/registracija'
  }
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
