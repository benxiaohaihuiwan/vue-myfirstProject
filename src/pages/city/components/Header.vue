<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <div class="iconfont city-back-icon">&#xe600;</div>
    </router-link>
  </div>
</template>

<script>
  export default {
    name:'CityHeader',

  }
</script>

<style lang="stylus" scoped>
  @import '~@/assets/styles/varibles.styl'
  .header
    position relative
    overflow hidden
    height 1.96rem
    line-height 1.96rem
    text-align center
    color #fff
    background $backcolor
    font-size 16px
    .city-back-icon
      position absolute
      left 0rem
      top 0rem
      width 1rem
      font-size 1.3rem
      color #fff
</style>
