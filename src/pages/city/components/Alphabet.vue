<template>
  <div>
    <ul class="list">
      <li class="item" v-for="item in letters"
          :key="item"
          :ref="item"
          @touchstart="handleTouchStart"
          @touchmove="handleTouchMove"
          @touchend="handleTouchEnd"
          @click="handleLetterClick">
        {{item}}
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name:'CityAlphabet',
    props:{
      cities: Object
    },
    computed:{
      letters (){
        const letters = []
        for(let i in this.cities){
          letters.push(i)
        }
        return letters
      }
    },
    data (){
      return {
        touchStatus: false,
        startY: 0,
        timer: null
      }
    },
    updated (){
      this.startY = this.$refs['A'][0].offsetTop
    },
    methods:{
      handleLetterClick (e){
        this.$emit('change',e.target.innerText)
        console.log(e.target.innerText)
      },
      handleTouchStart (){
        this.touchStatus = true
      },
      handleTouchMove (e){
        if(this.touchStatus){
          if(this.timer){
            clearTimeout(this.timer)
          }
          this.timer = setTimeout(() =>{
            const touchY = e.touches[0].clientY -27
            console.log("touchY---"+touchY)
            const index = Math.floor((touchY-this.startY)/21)
            if(index>=0 && index<=this.letters.length){
              this.$emit('change',this.letters[index])
            }
          },16)
        }
      },
      handleTouchEnd (){
        this.touchStatus = false
      }
    }
  }
</script>

<style lang="stylus" scoped>
  .list
    position absolute
    top 0rem
    right 0rem
    bottom 0rem
    display flex
    flex-direction column
    justify-content center
    .item
      text-align center
      list-style none
      color greenyellow
      width 2rem
</style>
