<template>
  <div>
    <div class="search">
      <input v-model="keyword" class="search-city" type="text" placeholder="输入城市名或拼音"/>
    </div>
    <div class="search-content" ref="search" v-show="keyword">
      <ul class="search-ul">
        <li class="search-li" v-for="item in list" ref="search" @click="handleLetClick(item.name)">
          {{item.name}}
        </li>
        <li class="search-li" v-show="hasNoData">
          数据没有匹配项
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  import {mapState,mapMutations} from 'vuex'
  import Bscroll from 'better-scroll'
  export default {
    name:'CitySearch',
    props:{
      cities:Object
    },
    computed:{
      hasNoData(){
        return !this.list.length
      }
    },
    methods:{
      handleLetClick (city){
        //this.$store.commit('changeCity',city)
        this.changeCity(city)
        this.$router.push('/')
      },
      ...mapMutations(['changeCity'])
    },
    data (){
      return {
        keyword:'',
        list:[],
        timer: null
      }
    },
    mounted (){
      this.scroll = new Bscroll(this.$refs.search)
    },
    watch: {
      keyword (){
        if(this.timer){
          clearTimeout(this.timer)
        }
        if(!this.keyword){
          this.list=[]
          return
        }
        this.timer = setTimeout(()=>{
          const result = []
          for(let i in  this.cities){
            this.cities[i].forEach((value)=>{
              if(value.spell.indexOf(this.keyword)> -1 ||
              value.name.indexOf(this.keyword)> -1){
                result.push(value)
              }
            })
          }
          this.list = result
        },100)
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import '~@/assets/styles/varibles.styl'
  .search-content
    z-index 1
    overflow hidden
    position absolute
    top 4.8rem
    left 0
    right 0rem
    bottom 0rem
    background #eee
    .search-ul
      margin .3rem
      padding 0rem
      .search-li
        list-style none
        background #fff
        text-align left

  .search
    height 1.72rem
    padding .1rem .3rem
    padding-left .1rem
    background green
    .search-city
      width 100%
      text-align center
      height 1.32rem
      line-height 1.32rem
      border-radius .6rem
      color #666
</style>
