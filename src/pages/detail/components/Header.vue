<template>
    <div>

        <router-link tag="div" to="/" v-show="showAbs" class="header-abs">
          <div class="iconfont iconfanhui back-icon"></div>
        </router-link>
        <div class="header-fixed"  v-show="!showAbs"
          :style="opacityStyle"
        >
          <router-link to="/">
            <div class="iconfont iconfanhui herder-fixed-back"></div>
          </router-link>
          景点详情
        </div>

    </div>
</template>

<script>
    export default {
        name: "DetailHeader",
        data(){
          return{
            showAbs: true, //是否显示Abs隐藏fxied用  高度滑向60后 反一反
            opacityStyle:{ //初始透明度为0
              opacity:0
            }
          }
        },
        methods:{
          handleScroll(e){
            console.log(document.documentElement.scrollTop) //滑动了多少高度
            let scrollTop = document.documentElement.scrollTop
            if(scrollTop >= 60){
              let opacity =scrollTop / 140
              opacity = opacity > 1 ? 1 : opacity
              this.opacityStyle = {
                opacity
              }
              this.showAbs = false
            }else{
              this.showAbs = true
            }
          }
        },
        activated(){
          window.addEventListener('scroll',this.handleScroll) //当屏幕滚动就触发
        },
        deactivated(){
          window.removeEventListener('scroll',this.handleScroll)
        }
    }
</script>
a
<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .header-abs
    position:absolute
    left:.2rem
    top:.2rem
    width:.8rem
    height:.8rem
    line-height :.8rem
    border-radius: .4rem
    text-align: center
    background: rgba(0,0,0,.8)
    .back-icon
      color: #fff
      font-size: .4rem
      margin-left : -.05rem

  .header-fixed
    position: fixed
    top: 0
    left: 0
    right: 0
    height: $headerHeight
    line-height: $headerHeight
    text-align: center
    color:  #fff
    background: $bgColor
    font-size: .32rem
    .herder-fixed-back
      color: #fff
      position: absolute
      top: 0
      left: 0
      width: .64rem
      text-align: center
      font-size: .4rem
</style>
