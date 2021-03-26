<template>
  <nav class="grid cols gap">
    <router-link id="link0" to="/"
      ><img src="@/assets/vectors/logo.svg"
    /></router-link>
    <router-link id="link1" to="/">illustrer</router-link>
    <router-link id="link2" to="/gallery">galerie</router-link>
    <router-link id="link3" to="/">acheter</router-link>
  </nav>
</template>

<style lang="scss">
nav {
  padding: 0 $unit;
  padding-bottom: 2px;
  width: 100%;
  grid-template-rows: 1fr;
  align-items: center;
  top: 0;
  left: 0;
  right: 0;
  position: fixed;
  z-index: 30000;
  mix-blend-mode: difference;
  pointer-events: none;

  a {
    grid-row: 1;
    display: block;
    padding: $unit 0;
    color: map-get($colors, 'offwhite');
    pointer-events: all;
  }

  img {
    width: 100%;
  }

  #link0 {
    grid-column: 1;
    justify-self: start;
  }
  #link1 {
    grid-column: 6 / 8;
    justify-self: start;
  }
  #link2 {
    grid-column: 8 / 12;
    justify-self: end;
  }
  #link3 {
    grid-column: 12 / 17;
    justify-self: end;
  }
}
</style>
