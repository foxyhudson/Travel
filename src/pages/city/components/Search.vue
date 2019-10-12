<template>
    <div>
      <div class="search">
        <input  v-model="keyword" class="search-input" type="text" placeholder="输入城市名或拼音">
      </div>
      <div v-show="keyword" class="serach-content" ref="serach">
        <ul>
          <li
            @click="handleCityClick(item.name)"
            class="search-time border-bottom" v-for ="item of list" :key="item.id" >{{item.name}}</li>
          <li v-show="hasNoData" class="search-time border-bottom">没有找到匹配数据</li>
        </ul>
      </div>
    </div>
</template>

<script>
    import Bscroll from "better-scroll"
    import {mapMutations} from 'vuex'
    export default {
        name: "CitySearch",
        props:{
          cities:Object
        },
        data(){
          return{
            keyword:"",
            list:[],
            timer:null, //节流
          }
        },

        computed:{
          hasNoData(){
            return !this.list.length
          }
        },
        mounted(){
          this.search = new Bscroll(this.$refs.wrapper, { mouseWheel: true, click: true, tap: true })
        },
        methods:{
          ...mapMutations({
            changeCity : 'changeCity'
          }),
          handleCityClick(city){
            // this.$store.commit('changeCity',city)
            this.changeCity(city)
            this.$router.push('/')
          }
        },
        watch:{
          keyword(){
            if(this.timer){
              clearTimeout(this.timer)
            }
            if(!this.keyword){
              this.list=[]
              return
            }
            this.timer = setTimeout(()=>{
              const result = []
              for (let i in this.cities){
                this.cities[i].forEach((value)=>{
                  if(value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1){
                    result.push(value)
                  }
                })
              }
              this.list =result
            },100)
          },
        }
    }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .search
    height: .72rem
    background: $bgColor
    padding: 0 .1rem
    .search-input
      box-sizing: border-box
      width: 100%
      height: .62rem
      line-height: .62rem
      text-align: center
      border-radius: .06rem
      color: #666
      padding : 0 .1rem
  .serach-content
    z-index: 1
    overflow: hidden
    position: absolute
    top: 1.58rem
    left: 0
    right: 0
    bottom: 0
    background: #eee
    .search-time
      height :.62rem
      line-height:.62rem
      padding-left:.2rem
      color:#666
      background: #fff
</style>
