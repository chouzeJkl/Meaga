<template>
  <div class="visualizer" :class="{hide: hide}">
    <canvas width="1024" height="100" ref="canvas"></canvas>
    <div class="mask"></div>
  </div>
</template>
<script>
// import visualizer from '@/helpers/visualizer'

export default {
  name: 'visualizer',
  mounted () {
    // visualizer.initialize(window.player_core, this.$refs.canvas)
  },
  computed: {
    hide () {
      return !this.$store.state.status.visualize
    }
  }
}
</script>
<style lang="scss" scoped>
@import '~scssinc';

.visualizer{
  display: none;
  position: absolute;
  bottom: 1px;
  left: 50%;
  z-index: 1;
  width: 1024px;
  height: 100px;
  overflow: hidden;
  pointer-events: none;
  transform: translateX(-50%);
  &.hide{
    opacity: 0;
  }
  canvas{
    position: absolute;
    top: 0;
    left: 0;
    width: 1024px;
    height: 100px;
    background-color: transparent;
  }
}
.mask{
  position: absolute;
  z-index: 2;
  top: 0;
  right: 1px;
  left: 1px;
  height: 100px;
  background-image: linear-gradient(transparent 0px, transparent 1px, $color_background 1px, $color_background 2px);
  background-position: 50% 0;
  background-repeat: repeat-y;
  background-size: 1022px 2px;
}
</style>
