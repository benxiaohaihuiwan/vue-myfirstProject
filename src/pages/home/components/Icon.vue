<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page,index) in pages" :key="index">
        <div class="icon" v-for="item in page" :key="item.id">
          <div class="icon-img">
            <img class="icon-img-content" :src="item.imgUrl"/>
          </div>
            <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
  export default {
    name: 'HomeIcon',
    props:{
      iconList1: Array
    },
    data (){
      return {
        swiperOption:{
          autoplay: false
        }
      }
    },
    computed:{
      pages (){
        const pages = []
        this.iconList1.forEach((item,index)=>{
          const page=Math.floor(index/8)
          if(!pages[page]){
            pages[page]=[]
          }
          pages[page].push(item)
        })
        return pages
      }
    }
  }
</script>

<style lang="stylus" scoped>
  import '~@/assets/styles/mixins.styl'
  .icons >>> .swiper-container
    height 0
    padding-bottom 50%
  .icon
    position relative
    overflow hidden
    float left
    width 25%
    padding-bottom 25%
    .icon-img
      position absolute
      top 0
      left 0
      right 0
      bottom .64rem
      box-sizing border-box
      padding .1rem
      .icon-img-content
        display block
        height 100%
        margin 0 auto
    .icon-desc
      position absolute
      left 0
      right 0
      bottom 0
      height .64rem
      line-height .64rem
      margin-bottom: 0px
      font-size: 12px;
      color #333
      text-align center
      ellipsis()
</style>
