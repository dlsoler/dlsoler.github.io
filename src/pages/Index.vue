<template>
  <q-page>
    <div class="row">
      <div class="col-xs-1 col-sm-1 col-md-2"></div>
      <div class="cols-xs-10 col-sm-10 col-md-10">
        <div id="name-container" class="column justify-center">
          <text-stroke text="DIEGO" :canvasWidth="450" />
          <text-fill text="SOLER" :canvasWidth="450" />
          <div id="subtitle">Desarrollador freelance</div>
        </div>
      </div>
    </div>
    
  </q-page>
</template>

<script lang="ts">
import { defineComponent} from 'vue';

import TextStroke from '../components/text_stroke.vue';
import TextFill from '../components/text_fill.vue';

export default defineComponent({
  name: 'PageIndex',
  components: {
    'text-stroke': TextStroke,
    'text-fill': TextFill
  },
  setup() {
    return {};
  }
});
</script>

<style lang="scss">
#name-container {
  height: calc(100vh - 50px);
}
#developer-name {
  color: #fff;
  font-family: 'Montserrat';
  font-size: 120px;
  font-weight: 900;
  text-transform: uppercase;
  text-align: left;
  letter-spacing: 0.5ex;
}
#developer-lastname {
  color: #fff;
  font-family: 'Montserrat';
  font-size: 120px;
  font-weight: 900;
  text-transform: uppercase;
  text-align: left;
  letter-spacing: 0.5ex;
}

#subtitle {
  color: #f0f0f0;
  font-family: 'Montserrat';
  text-align: left;
}
</style>
