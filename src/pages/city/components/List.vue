<template>
   <div class="list" ref="wrapper">
     <div>
       <div class="area">
         <div class="title border-topbottom">当前城市</div>
         <div class="button-list">
           <div class="button-wrapper" >
             <div class="button">北京</div>
           </div>
         </div>
       </div>
       <div class="area">
         <div class="title border-topbottom">热门城市</div>
         <div class="button-list" >
           <div class="button-wrapper" v-for="(item,index) of hotCities" :key="item.id">
             <div class="button">{{item.name}}</div>
           </div>
         </div>
       </div>
       <div class="area border-topbottom">
         <div v-for="(item,key) of cities" :key="key">
           <div class="title border-topbottom">{{key}}</div>
<!--           <div v-for="(item,index) of getCityname({{item}})">-->
           <div class="item-list" >
             <div class="item border-bottom" v-for="item2 of item" :key="item2.id">{{item2.name}}</div>
           </div>
         </div>
       </div>
     </div>
   </div>
</template>

<script>
  import Bscroll from "better-scroll"
  export default {
        name: "CityList",
        props:{
          hotCities:  Array,
          cities: Object
        },
        mounted() {
          this.scroll = new Bscroll(this.$refs.wrapper)
        },
        computed:{
          getCity(){

          },
        }
  }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .border-topbottom
    &:before
      border-color: #ccc
    &:after
      border-color: #ccc
  .border-bottom
    &:before
      border-color: #ccc
  .list
    overflow:hidden  //用了后不能上下拖动了 之后配个一个插件即可
    position:absolute
    top:1.58rem //留给头部
    left:0
    right:0
    bottom:0
    .title
      line-height: .54rem
      background: #eee
      padding-left: .2rem
      color:#666
      font-size: .26rem
    .button-list
      padding: .1rem .6rem .1rem .1rem //为拼音留位置
      overflow: hidden
      .button-wrapper
        float: left
        width: 33.33%
        .button
          margin: .1rem
          padding: .1rem 0
          text-align: center
          border: .02rem solid #ccc
          border-radius: .03rem
    .item-list
      .item
        line-height:.76rem
        padding-left: .2rem
</style>
