<template>
  <main id="illu-details" class="grid cols rows gap padding" draggable="false">
    <section
      draggable="false"
      id="thumb-scroller"
      class="scroller"
      ref="thumbScroller"
    >
      <Image
        :src="illu.src"
        class="thumb"
        v-for="(illu, index) in illustrations"
        :key="`thumb${index}`"
        :id="`thumb${index}`"
        @click="onIlluClick(index)"
        draggable="false"
      />
    </section>
    <div id="indicator-container">
      <div id="indicator"></div>
    </div>
    <section
      draggable="false"
      id="illu-scroller"
      class="scroller"
      ref="illuScroller"
    >
      <Image
        :src="illu.src"
        class="illu"
        v-for="(illu, index) in illustrations"
        :key="`illu${index}`"
        :id="`illu${index}`"
        @click="onIlluClick(index)"
        draggable="false"
      />
    </section>
  </main>
</template>

<script>
import Image from '@/components/GalleryImage';
import gsap, { Power2 } from 'gsap';

import img1 from '@/assets/img/1.jpg';
import img2 from '@/assets/img/2.jpg';
import img3 from '@/assets/img/3.jpg';
import img4 from '@/assets/img/4.jpg';
import img5 from '@/assets/img/5.jpg';
import img6 from '@/assets/img/6.jpg';

const { easeInOut } = Power2;

export default {
  name: 'IllustrationDetails',
  components: {
    Image,
  },
  data: () => ({
    illustrations: [
      {
        src: img1,
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
      {
        src: img2,
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
      {
        src: img3,
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
      {
        src: img4,
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
      {
        src: img5,
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
      {
        src: img6,
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
      {
        src:
          'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
      {
        src:
          'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
      {
        src:
          'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
      {
        src:
          'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
      {
        src:
          'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
      {
        src:
          'https://mir-s3-cdn-cf.behance.net/project_modules/fs/0e6625105677035.5f7e301243b9a.jpg',
        author: 'blksk',
        word: {
          word: 'Labyrinthe',
          type: 'n.m',
          defintion: `
          Réseau compliqué de chemins, de galeries dont on a du mal à trouver l'issue.
          Petit bosquet aux allées entrelacées formant des méandres compliqués, au milieu d'un parc ou d'un jardin.
          Appareil constitué d'un ensemble d'allées et d'impasses, employé pour étudier les comportements d'apprentissage chez l'animal.
          `,
        },
      },
    ],
    scrollIndex: 0,
    yIllu: 0,
    mouse: {
      originPos: { x: 0, y: 0 },
      currentPos: { x: 0, y: 0 },
      grabVelocity: { x: 0, y: 0 },
      frictionCoef: 0.85,
      dragging: false,
      clicking: false,
    },
    frameId: null,
  }),
  computed: {
    illuHeight() {
      return (
        -this.$refs.illuScroller.querySelector('img').getBoundingClientRect()
          .height - 20
      );
    },
    thumbHeight() {
      return (
        -this.$refs.thumbScroller.querySelector('img').getBoundingClientRect()
          .height - 20
      );
    },
    grabOffset() {
      const { currentPos, originPos } = this.mouse;
      return currentPos.y - originPos.y;
    },
  },
  watch: {
    'mouse.currentPos': function(next, prev) {
      this.mouse.grabVelocity = {
        x: next.x - prev.x,
        y: next.y - prev.y,
      };
    },
  },
  methods: {
    scrollToIllu(index) {
      const { illuScroller, thumbScroller } = this.$refs;
      const maxIndex = this.illustrations.length - 1;
      this.scrollIndex = index < 0 ? 0 : index > maxIndex ? maxIndex : index;
      console.log(index);
      console.log(this.scrollIndex);
      gsap.to(illuScroller, {
        duration: 0.6,
        y: this.illuHeight * this.scrollIndex,
        ease: easeInOut,
      });
      gsap.to(thumbScroller, {
        duration: 0.6,
        y: this.thumbHeight * this.scrollIndex,
        ease: easeInOut,
      });
    },
    translateImage(target, y, duration) {
      gsap.to(target, {
        duration,
        y,
        ease: easeInOut,
      });
    },
    onIlluClick(index) {
      this.scrollToIllu(index);
    },
    onResize() {
      this.scrollToIllu(this.scrollIndex);
    },
    onScroll({ deltaY }) {
      const index = deltaY < 0 ? this.scrollIndex - 1 : this.scrollIndex + 1;
      if (index >= 0 && index <= this.illustrations.length - 1) {
        this.scrollToIllu(index);
      }
    },
    onMouseDown(e) {
      this.mouse.clicking = true;
      this.mouse.originPos = { x: e.clientX, y: e.clientY };
    },
    onMouseMove(e) {
      if (!this.mouse.dragging && this.mouse.clicking) {
        this.mouse.dragging = true;
      }
      this.mouse.currentPos = { x: e.clientX, y: e.clientY };
    },
    onMouseUp() {
      this.mouse.clicking = false;
      if (this.mouse.dragging) {
        this.mouse.dragging = false;
        this.snapOnGrabRelease();
      }
    },
    snapOnGrabRelease() {
      const illuCount = this.illustrations.length - 1;
      const currentY = this.scrollIndex * this.illuHeight + this.grabOffset;
      const totalHeight = illuCount * this.illuHeight;
      const scrolledRatio = currentY / totalHeight;
      const newIndex = scrolledRatio * illuCount;
      this.scrollToIllu(Math.round(newIndex));
    },
    applyGrabTransform() {
      const { illuScroller, thumbScroller } = this.$refs;
      if (this.mouse.dragging) {
        this.yIllu = this.scrollIndex * this.illuHeight + this.grabOffset;
        const yThumb =
          this.scrollIndex * this.thumbHeight +
          (this.grabOffset * this.thumbHeight) / this.illuHeight;
        this.translateImage(illuScroller, this.yIllu, 0);
        this.translateImage(thumbScroller, yThumb, 0);
      }
    },
    animate() {
      this.applyGrabTransform();
      this.frameId = window.requestAnimationFrame(this.animate.bind(this));
    },
  },
  mounted() {
    window.addEventListener('resize', this.onResize);
    window.addEventListener('wheel', this.onScroll);
    window.addEventListener('mousedown', this.onMouseDown);
    window.addEventListener('mousemove', this.onMouseMove);
    window.addEventListener('mouseup', this.onMouseUp);
    this.frameId = requestAnimationFrame(this.animate.bind(this));
  },
  unmounted() {
    window.removeEventListener('resize', this.onResize);
    window.removeEventListener('wheel', this.onScroll);
    window.removeEventListener('mousedown', this.onMouseDown);
    window.removeEventListener('mousemove', this.onMouseMove);
    window.removeEventListener('mouseup', this.onMouseUp);
    window.cancelAnimationFrame(this.frameId);
  },
};
</script>

<style lang="scss">
#illu-details {
  height: 100vh;
  overflow: hidden;
}

.scroller {
  overflow: visible;
  scroll-snap-type: y mandatory;

  &::-webkit-scrollbar {
    display: none;
  }
}

#illu-scroller {
  grid-column: 6 / 12;
  grid-row: 2 / -1;

  .illu {
    width: 100%;
    margin: $unit 0;
    max-height: calc(79.25vh);
    scroll-snap-align: center;

    &:first-child {
      margin-top: 0;
    }
  }
}

#thumb-scroller {
  grid-column: 2 / 3;
  grid-row: 1 / -1;

  .thumb {
    width: 100%;
    margin: $unit 0;
    scroll-snap-align: center;

    $end-margin: calc(50vh - (50% * 1.53125) - 20px);

    &:first-child {
      margin-top: $end-margin;
    }
  }
}

#indicator-container {
  grid-column: 2 / span 1;
  grid-row: 5 / span 2;
  height: 100%;
  z-index: 2;
  display: flex;
  align-items: center;
  justify-content: center;

  #indicator {
    border: 1px solid map-get($colors, 'grey');
    width: 100%;
    height: calc((100vw - var(--unit) * 17) / 16 * var(--img-ratio));
    transform: rotate(90deg);
  }
}
</style>
