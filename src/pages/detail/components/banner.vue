<template>
  <div class="banner">
    <img class="banner-img" src="http://imgs.qunarzz.com/p/tts0/1807/6a/fbc036af8043b02.jpg_262x238_bb11eed8.jpg"/>
    <div class="banner-info">
      <div class="banner-title">333333333333222222222222</div>
      <div class="banner-number"><span class="iconfont arrow-icon">&#xe601;</span>32</div>
    </div>
  </div>
</template>

<script>
  export default {
    name:'DetailBanner'
  }
</script>

<style lang="stylus" scoped>
  .banner
    position relative
    overflow hidden
    padding-bottom 55%
    height 0rem
    .banner-img
      width 100%
    .banner-info
      display flex
      position absolute
      left 0rem
      right 0rem
      bottom 0rem
      line-height .6rem
      background-image: linear-gradient(top, rgba(0,0,0,0),fgba(0,0,0,0.8))
      .banner-title
        flex 1
        padding .4rem
      .banner-number
        margin .4rem
        height .4rem
        line-height .4rem
        border-radius .2rem
</style>
