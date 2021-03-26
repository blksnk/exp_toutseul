<template>
  <img :src="src" :alt="alt" ref="img" :style="style" draggable="false" />
</template>

<script>
export default {
  props: {
    src: String,
    alt: {
      type: String,
      default: '',
    },
    ratio: {
      type: Number,
      default: 1.53125,
    },
  },
  data: () => ({
    style: {
      height: 'auto',
    },
  }),
  methods: {
    setImagesToRatio() {
      //get first image in gallery
      //get current width & generate height
      const { width } = this.$refs.img.getBoundingClientRect();
      const height = width * this.$props.ratio;
      //apply height
      this.style.height = `${height}px`;
    },
  },
  mounted() {
    this.setImagesToRatio();
    //attach resize event
    window.addEventListener('resize', this.setImagesToRatio);
  },
  unmounted() {
    window.removeEventListener('resize', this.setImagesToRatio);
  },
};
</script>
