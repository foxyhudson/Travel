<template>
    <div>
      <home-header :city="city"></home-header>
      <home-swiper :swiperList="swiperList"></home-swiper>
      <home-icons :iconList="iconList"></home-icons>
      <home-recommend :recommendList="recommendList"></home-recommend>
      <home-weekend :weekendList="weekendList"></home-weekend>
    </div>
</template>

<script>
    import HomeHeader from './components/Header'
    import HomeSwiper from './components/Swiper'
    import HomeIcons from './components/icons'
    import HomeRecommend from './components/Recommend'
    import HomeWeekend from './components/Weekend'
    import axios from 'axios'
    import {mapState} from 'vuex'
    // import HomeSwiper from './components/Swiper'
    //引入组件
    export default {
        name: "Home",
        components:{
          HomeHeader,
          HomeSwiper,
          HomeIcons,
          HomeRecommend,
          HomeWeekend
        },
        data(){
          return{
            lastcity:'',
            swiperList: [],
            iconList:[],
            recommendList:[],
            weekendList:[]
          }
        },
        computed:{
          ...mapState(['city'])
        },
        methods:{

          swiperListInfo(){
            axios.get('api/index.json?city=' + this.city)
              .then(this.getSwiperList)
          },

          getSwiperList(res){
            res = res.data
            if(res.ret && res.data){
              const data = res.data
              this.swiperList = data.swiperList
              this.iconList = data.iconList
              this.recommendList = data.recommendList
              this.weekendList = data.weekendList
            }
          }
        },
        mounted(){
          this.lastcity = this.city
          this.swiperListInfo()

        },
        activated() {
          if(this.lastcity !== this.city){
            this.lastcity = this.city
            this.swiperListInfo()
          }
        }
    }
</script>

<style lang="stylus" scoped>

</style>
