<template>
  <main id="gallery" class="grid cols rows gap padding">
    <button id="filter-button">filtrer</button>
    <section id="image-container" ref="container">
      <article v-for="(image, index) in images" :key="image + index">
        <img :src="image" alt="" :style="thumbnailStyle" />
      </article>
    </section>
  </main>
</template>

<script>
import img1 from '@/assets/img/1.jpg';
import img2 from '@/assets/img/2.jpg';
import img3 from '@/assets/img/3.jpg';
import img4 from '@/assets/img/4.jpg';
import img5 from '@/assets/img/5.jpg';
import img6 from '@/assets/img/6.jpg';

export default {
  name: 'Gallery',
  data: () => ({
    thumbnailRatio: 1.53125,
    thumbnailStyle: {
      height: 'auto',
    },
    images: [
      img1,
      img2,
      img3,
      img4,
      img5,
      img6,
      'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
      'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
      'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
      'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
      'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
      'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
    ],
  }),
  methods: {
    setImagesToRatio() {
      window.requestAnimationFrame(() => {
        //get first image in gallery
        const img = this.$refs.container.querySelector('img');
        if (img && img !== null && img !== undefined) {
          //get current width & generate height
          const { width } = img.getBoundingClientRect();
          const height = width * this.thumbnailRatio;
          //apply height
          this.thumbnailStyle.height = `${height}px`;
        }
      });
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

<style lang="scss">
#gallery {
  height: 100vh;
  overflow: hidden;
}
#image-container {
  grid-column: 3 / -3;
  grid-row: 1 / -1;
  padding-top: calc(10vh + var(--unit));
  display: flex;
  align-items: flex-start;
  gap: $unit;
  flex-wrap: wrap;
  overflow-y: scroll;
  position: relative;
  top: -$unit;
  height: 100vh;

  &::-webkit-scrollbar {
    display: none;
  }

  article {
    width: calc((100% / 3) - (var(--unit) * 2 / 3));
    height: min-content;

    img {
      width: 100%;
    }
  }
}

#filter-button {
  grid-column: 2;
  grid-row: 2;
  height: min-content;
  border: none;
  text-align: right;
}
</style>
