<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe600;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe633;</span>
      输入景点内容</div>
    <router-link to="/city">
      <div class="header-right">{{this.city}}
        <span class="iconfont arrow-icon">&#xe601;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
  import {mapState} from 'vuex'
  export default {
    name:'HomeHeader',
    computed: {
      ...mapState(['city'])
    }
  }
</script>

<style lang="stylus" scoped>
  @import '~@/assets/styles/varibles.styl'
  .header
    display: flex
    line-height: 1.96rem
    color: #fff
    background: $backcolor
    .header-letf
      width: .72rem
      float: left
      .back-icon
        text-align center
        font-size .4rem
    .header-input
      flex 1
      margin-left .4rem
      margin-top .3rem
      padding-bottom .3rem
      padding-left .4rem
      background #fff
      height 1.22rem
      border-radius .1rem
      color #000
      font-size 14px
    .header-right
      width: 5.24rem
      float: right
      text-align: center
      color #fff
      .arrow-icon
        font-size .84rem
</style>
