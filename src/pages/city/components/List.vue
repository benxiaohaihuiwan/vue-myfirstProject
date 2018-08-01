<template>
  <div class="list" ref="wrapper">
    <div >
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list" >
          <div class="button-wrapper" v-for="item in hotCities" :key="item.id" @click="handleLetClick(item.name)">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
    <div class="area" v-for="(item,key) in cities" :key="key" :ref="key">
      <div class="title border-topbottom">{{key}}</div>
      <div class="item-list">
        <div class="item border-bottom" v-for="innerItem in item" :key="innerItem.id" @click="handleLetClick(innerItem.name)"
        >{{innerItem.name}}</div>
      </div>
      </div>
    </div>
  </div>
</template>

<script>
  import {mapState,mapMutations} from 'vuex'
  import Bscroll from 'better-scroll'
  export default {
    name:'CityList',
    props:{
      cities : Object,
      hotCities: Array,
      letter: String
    },
    computed:{
      ...mapState(['city'])
    },
    methods:{
      handleLetClick (city){
        //this.$store.commit('changeCity',city)
        this.changeCity(city)
        this.$router.push('/')
      },
      ...mapMutations(['changeCity'])
    },
    mounted (){
      this.scroll = new Bscroll(this.$refs.wrapper)
    },
    watch:{
      letter (){
        if(this.letter){
          const element = this.$refs[this.letter][0]
          this.scroll.scrollToElement(element)
        }
      }
    },
  }
</script>

<style lang="stylus" scoped>
  .border-topbottom
    :before
      border-color #666
    :after
      border-color #ccc
  .list
    overflow hidden
    position absolute
    left 0rem
    right 0rem
    bottom 0
    top 4.72rem
    .title
      line-height 1.54rem
      background #eee
      padding-left .2rem
      color #666
      font-size 16px
    .button-list
      padding .1rem .6rem .1rem .1rem
      overflow hidden
      .button-wrapper
        float left
        width 33.3%
        .button
          margin .1rem
          padding .1rem 0rem
          text-align center
          border .02rem solid #ccc
          border-radius .06rem
    .item-list
      .item
        padding-left .2rem
        line-height 1.84rem
        height 1.84rem
</style>
