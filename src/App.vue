<template>
  <div id="bg-image"></div>
  <router-view />
</template>
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'App'
})
</script>
<style lang="scss">
#bg-image {
  background: url(/images/programming_code.jpg) center center no-repeat  cover transparent;
}
</style>
