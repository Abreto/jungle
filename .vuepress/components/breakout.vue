<template>
  <div class="breakout-container" ref="container" :style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }">
    <div class="breakout-content" ref="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'breakout',
  methods: {
    enhance() {
      const container = this.$refs.container
      const content = this.$refs.content
      const clientWidth = document.documentElement.clientWidth
      const originalWidth = container.offsetWidth

      // container.style.width = `${clientWidth}px`
      // container.style.maxWidth = `${clientWidth}px`
      content.style.maxWidth = `${clientWidth * 0.9}px`
      // container.style.marginLeft = `${-(clientWidth - originalWidth) / 2}px`
    }
  },
  mounted() {
    this.enhance()
    window.addEventListener('resize', this.enhance)
  },
  beforeDestroy: function () {
    window.removeEventListener('resize', this.enhance)
  },
}
</script>

<style lang="stylus">
.breakout-container
  white-space: nowrap;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: center;
.breakout-container .breakout-content
  margin: auto
</style>
