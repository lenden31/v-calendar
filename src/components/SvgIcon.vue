<template>
  <svg
    class="vc-svg-icon"
    :width="width"
    :height="height"
    :viewBox="viewBox"
    v-on="$listeners"
  >
    <path :d="path" />
  </svg>
</template>

<script>
const _defSize = '26px';
const _defViewBox = '0 0 32 32';

const icons = {
  'left-arrow': {
    viewBox: '0 0 16 16',
    path:
      'M10.0498 3.10059L5.10006 8.05033L10.0498 13.0001',
  },
  'right-arrow': {
    viewBox: '0 0 16 16',
    path:
      'M5.9502 12.8994L10.8999 7.94967L5.95019 2.99992',
  },
};

export default {
  props: ['name'],
  data() {
    return {
      width: _defSize,
      height: _defSize,
      viewBox: _defViewBox,
      path: '',
      isBaseline: false,
    };
  },
  mounted() {
    this.updateIcon();
  },
  watch: {
    name() {
      this.updateIcon();
    },
  },
  methods: {
    updateIcon() {
      const icon = icons[this.name];
      if (icon) {
        this.width = icon.width || _defSize;
        this.height = icon.height || _defSize;
        this.viewBox = icon.viewBox;
        this.path = icon.path;
      }
    },
  },
};
</script>

<style lang="postcss" scoped>
.vc-svg-icon {
  display: inline-block;
  stroke: currentColor;
  stroke-width: 1;
  & path {
    fill: none;
  }
}
</style>
