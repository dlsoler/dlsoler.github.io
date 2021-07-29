<template>
  <q-toolbar id="top-toolbar" class="bg-transparent">
    <q-btn
      v-if="collapseMenu"
      id="menu-button"
      flat
      dense
      round
      icon="menu"
      aria-label="Menu"
      @click="toggleDrawer"
      text-color="#dcab7eff"
    />

    <img class="q-ml-xl" id="logo-img" src="images/logo-d-1.png">

    <q-space />

    <q-tabs id="top-tabs" v-if="!collapseMenu" v-model="tab" shrink no-caps>
        <q-tab name="tab1" label="Home" />
        <q-tab name="tab2" label="About" />
        <q-tab name="tab3" label="Portfolio" />
        <q-tab name="tab4" label="Testimonials" />
        <q-tab name="tab5" label="News" />
        <q-tab name="tab6" label="Contact" />
      </q-tabs>
  </q-toolbar>
</template>

<script lang="ts">
import { defineComponent, ref, computed } from 'vue'
import { useQuasar } from 'quasar'


export const TOGGLE_DRAWER_EVENT = 'toggle-drawer';

export default defineComponent({
  name: 'TopToolbar',
  methods: {
    toggleDrawer() {
      this.$emit(TOGGLE_DRAWER_EVENT);
    }
  },
  setup () {
    const $q = useQuasar();
    const collapseMenu = computed((): boolean => ($q.screen.name === 'xs' || $q.screen.name === 'sm'));
    return {
      tab: ref(''),
      collapseMenu
    };
  }
})
</script>

<style lang="scss">
#top-toolbar {
  font-size: 15px;
}
#logo-img {
  display: inline-block;
  height: 34px;
  width: auto;
}
#menu-button {
  margin-right: 30px;
  i {
    color: $bronze-color;
  }
}

#top-tabs {
  .q-tab__label {
    font-size: 15px;
    font-family: 'Montserrat'
  }
}
</style>
