<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="bg-transparent">
      <top-toolbar v-on:toggle-drawer="toggleDrawer"/>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      elevated
      class="bg-grey-10 text-white"
      behavior="mobile"
    >
      <q-list class="bg-grey-9">
        <q-item>
          <q-item-label
            header
            class="text-grey-5"
          >
          <span>Menu</span>
          </q-item-label>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">

import { defineComponent, ref } from 'vue'
import TopToolbar from '../components/top_toolbar.vue'


export default defineComponent({
  name: 'MainLayout',

  components: {
    'top-toolbar': TopToolbar,
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
