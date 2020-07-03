<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: "Scroll",
  props: {
    probeType: {
      type: Number,
      default: 0
    },
    // pullUpLoad: {
    //   type: Boolean,
    //   default: false
    // }
    
  },
  data() {
    return {
      scroll: null
    }
  },
  mounted() {
    this.scroll = new BScroll(this.$refs.wrapper, {
      click: true,
      probeType: this.probeType,
      pullUpLoad: true
    })
    this.scroll.on('scroll', (position) => {
      this.$emit('scroll', position)
    })
    // 监听上拉
    this.scroll.on('pullingUp', () => {
      this.$emit('pullingUp') 
      
    })
    this.scroll.scrollTo(0, 0)
  },
  methods: {
    finishPullUp() {
      this.scroll.finishPullUp()
    }
  }
}
</script>

<style scoped>

</style>