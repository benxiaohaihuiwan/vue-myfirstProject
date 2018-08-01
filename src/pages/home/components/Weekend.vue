<template>
  <div>
    <div class="recommend-title">周末去哪儿</div>
    <ul>
      <li class="item" v-for="(item,index) in recommendList2" :key="index">
        <div class="item-week-img">
          <img class="item-img" :src="item.imgUrl"></img>
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.info}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name:"HomeWeekend",
    props: {
      recommendList2: Array
    }
  }
</script>

<style lang="stylus" scoped>
  .recommend-title
    margin-top .3rem
    line-height 1.5rem
    background #eee
    text-indent .2rem
  .item
    list-style none
  .item-week-img
    overflow hidden
    height 0
    padding-bottom 34%
    margin-left -47px
    .item-img
      width 100%
  .item-info
    padding .1rem
    margin-left -47px
    .item-title
      line-height .89rem
      font-size 16px
    .item-desc
      line-height .19rem
      color #ccc
      font-size 12px
</style>
