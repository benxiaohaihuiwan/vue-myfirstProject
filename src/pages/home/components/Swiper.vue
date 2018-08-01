<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="this.showLength">
      <swiper-slide  v-for="item in swiperList1" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" />
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
  export default {
    name:'HomeSwiper',
    props:{
      swiperList1: Array
    },
    computed:{
      showLength (){
        return this.swiperList1.length
      }
    },
    data() {
      return{
        swiperOption:{
          pagination:'.swiper-pagination',
          loop:true
        }
      }
    }
  }
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background #fff !important
  .wrapper
    overflow hidden
    width 100%
    height 0
    padding-bottom 45%
    background gainsboro
    .swiper-img
      width:100%
      height: 160px
</style>
