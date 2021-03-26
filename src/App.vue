<template>
  <Nav />
  <router-view />
</template>

<script>
import '@/styles/fonts.scss';
import Nav from '@/components/Nav.vue';
export default {
  name: 'App',
  components: {
    Nav,
  },
};
</script>

<style lang="scss">
#app {
  background-color: map-get($colors, 'offwhite');
}
</style>
