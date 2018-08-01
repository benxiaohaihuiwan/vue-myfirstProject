<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul>
      <router-link tag="li"
         class="item" v-for="(item,index) in recommendList1" :key="index"
                   :to="'/detail/'+item.id">
          <img class="item-img" :src="item.imgUrl"></img>
          <div class="item-info">
            <p class="item-title">{{item.title}}</p>
            <p class="item-desc">{{item.info}}</p>
            <button class="item-button">查看详情</button>
          </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
  export default {
    name:"HomeRecommend",
    props:{
      recommendList1: Array
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
    height 5.8rem
    overflow hidden
    display flex
    margin-left -47px
    .item-img
      width 6rem
      height 100%
      padding .2rem
    .item-info
      flex 1
      padding .1rem
      .item-title
        line-height .89rem
        font-size 16px
      .item-desc
        line-height .19rem
        color #ccc
        font-size 12px
      .item-button
        background #ff3333
        padding .1rem
        border-radius .05rem
</style>
