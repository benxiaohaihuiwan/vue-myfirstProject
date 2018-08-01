<template>
  <div>
    <home-header></home-header>
    <home-swiper :swiperList1="swiperList1"></home-swiper>
    <home-icon :iconList1="iconList"></home-icon>
    <home-recommend :recommendList1="recommendList"></home-recommend>
    <home-weekend :recommendList2="recommendList"></home-weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcon from './components/Icon'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
export default {
  name:'Home',
  data (){
    return{
      swiperList1: [],
      iconList: [],
      recommendList: [],
      lastCity:''
    }
  },
  components:{
    HomeHeader,
    HomeSwiper,
    HomeIcon,
    HomeRecommend,
    HomeWeekend
  },
  methods:{
    getHomeInfo (){
      axios.get('./api/index.json')
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc(res){
      res=res.data
      if(res.ret && res.data){
        this.swiperList1=res.data.swiperList
        this.iconList = res.data.iconList
        this.recommendList = res.data.recommendList
      }
      console.log(res);
    }
  },
  mounted (){
    this.lastCity = this.city
    this.getHomeInfo()
  },
  activited (){
    if(this.lastCity !== this.city){
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }
}
</script>

<style>

</style>
