<template>
   <div class="header">
     <div class="header-left">
       <div class="iconfont iconfanhui back-icon"></div>
     </div>
     <div class="header-input">
       <span class="iconfont iconsousuo"></span>
       输入城市/景点/游玩主题</div>
     <router-link to="/city">
       <div class="header-right">
         <span class="header-right-font">{{city}}</span>
         <span class="iconfont iconjiantou_xia arrow-icon"></span>
       </div>
     </router-link>
   </div>
</template>

<script>
    import {mapState ,mapGetters} from 'vuex'
    export default {
        name: "HomeHeader",
        computed:{
          ...mapState(['city']),  //把state里的city映射过来
            ...mapGetters(['doubleCity'])
        }
        // props:{
        //   city:String
        // }
    }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  @import "~styles/mixins.styl"
  .header
    display:  flex
    line-height: $headerHeight
    background : $bgColor
    color: #fff
    .header-left
      width: .64rem
      float:  left
      .back-icon
        text-align: center
        font-size: .4rem
    .header-input
      flex:1  //自动撑开
      background: #fff
      height: .64rem
      line-height: .64rem
      margin-top: .12rem
      margin-left: .2rem
      border-radius :.1rem
      color: #ccc
      padding-left: .1rem

    .header-right
      color :#fff
      min-width: 1.04rem
      padding: 0.1rem
      float:  right
      text-align: center
      .arrow-icon
        font-size: .05rem
</style>
