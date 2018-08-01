<template>
  <div>
    <city-header></city-header>
    <city-search :cities="cities"></city-search>
    <city-list :cities="cities" :hotCities="hotCities" :letter="letter"></city-list>
    <city-alphabet :cities="cities"
    @change="handleLetterChange">
    </city-alphabet>
  </div>

</template>

<script>
  import CityHeader from './components/Header'
  import CitySearch from './components/Seach'
  import CityList from './components/List'
  import CityAlphabet from './components/Alphabet'
  import axios from 'axios'
  export default {
    name: 'City',
    components:{
      CityHeader,
      CitySearch,
      CityList,
      CityAlphabet
    },
    data (){
      return {
        cities:{},
        hotCities:[],
        letter:''
      }
    },
    methods: {
      getCityInfo (){
        axios.get('./api/city.json')
          .then(this.handleGetCitySucc)
      },
      handleGetCitySucc (res){
        res = res.data
        if(res.ret && res.data){
          this.cities = res.data.cities
          this.hotCities = res.data.hotCities
        }
        console.info(res)
      },
      handleLetterChange (letter){
        this.letter = letter
      }
    },
    mounted (){
      this.getCityInfo()
    }
  }
</script>

<style lang="stylus" scoped>

</style>
