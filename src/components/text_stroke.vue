<template>
  <div class="text-stroke">
    <canvas ref="textStrokeCanvas" class="text-stroke-canvas"></canvas>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue';

import {} from 'css-font-loading-module';

export default defineComponent({
  name: 'TextStroke',
  props: {

    text: {
      type: String,
      required: true
    },
    canvasWidth: {
      type: Number,
      required: true
    }
  },
  setup(props) {
    const textStrokeCanvas = ref(null);

    onMounted(() => {
      const fontFace: FontFace = new FontFace('Montserrat', 'url(https://fonts.gstatic.com/s/montserrat/v15/JTURjIg1_i6t8kCHKm45_bZF3gnD_g.woff2)');

      fontFace.load().then(
        () => {
          // Ready to use the font in a canvas context
          // the DOM element will be assigned to the ref after initial render
          if (textStrokeCanvas.value === null) {
            return;
          }
          const value = textStrokeCanvas.value as unknown
          const canvas: HTMLCanvasElement = value as HTMLCanvasElement;
          canvas.width = props.canvasWidth;
          
          const ctx = canvas.getContext('2d') as CanvasRenderingContext2D;
          if (ctx === null) return false;
          ctx.font = '120px Montserrat';
          ctx.strokeStyle = '#fff';
          ctx.strokeText(props.text, 0, 120, 400);
          return true;
        },
        (err) => console.error(err)
      );
    })

    return {
      textStrokeCanvas
    }
  }
})
</script>
<style lang="scss">
</style>
