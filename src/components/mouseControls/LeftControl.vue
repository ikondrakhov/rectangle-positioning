<template>
  <MouseControl id="left-control" :onDrag="LeftDragProcess" />
</template>

<script>
import MouseControl from "./MouseControl.vue";

export default {
  name: "LeftControl",
  components: {
    MouseControl,
  },
  methods: {
    LeftDragProcess(e) {
      this.$store.commit(
        "setWidth",
        this.$store.state.left +
          this.$store.state.offsetX +
          this.$store.state.width -
          e.pageX
      );
      this.$store.commit("setLeft", e.pageX - this.$store.state.offsetX);
    },
  },
};
</script>

<style scoped lang="scss">
@use 'sass:math';
@import "../../styles/styles.scss";

#left-control {
  position: absolute;
  top: 50% - math.div($control-rect-height, 2);
  left: math.div(-$control-rect-width, 2);
  width: $control-rect-width;
  height: $control-rect-height;
  background-color: $control-bc;
}
</style>
