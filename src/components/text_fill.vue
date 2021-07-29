<template>
  <div class="text-fill">
    <canvas ref="textFillCanvas" />
  </div>
</template>

<script lang="ts">
import { defineComponent,ref, onMounted } from 'vue'
import {} from 'css-font-loading-module';

export default defineComponent({
  name: 'TextFill',
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
    const textFillCanvas = ref(null);

    onMounted(() => {
      const fontFace: FontFace = new FontFace('Montserrat', 'url(https://fonts.gstatic.com/s/montserrat/v15/JTURjIg1_i6t8kCHKm45_bZF3gnD_g.woff2)');
      fontFace.load()
        .then(
          () => {
            // Now is ready to use the font in a canvas context
            // the DOM element will be assigned to the ref after initial render
            if (textFillCanvas.value === null) return;

            const value = textFillCanvas.value as unknown;
            const canvas: HTMLCanvasElement = value as HTMLCanvasElement;

            canvas.width = props.canvasWidth;
            const ctx = canvas.getContext('2d') as CanvasRenderingContext2D;
            if (ctx === null) return false;
            ctx.font = '120px Montserrat';

            const gradient = ctx.createLinearGradient(0,0, 0,200);
            gradient.addColorStop(0, 'rgba(255,255,255,0.85');
            // gradient.addColorStop(.5, 'cyan');
            gradient.addColorStop(1, 'rgba(255,255,255,0.3)');
            ctx.fillStyle = gradient;
            ctx.fillText(props.text, 0, 120, 400);
            return true; 
          },
          (err) => console.error(err)
        );
    });

    return {
      textFillCanvas
    }
  }
})
</script>
