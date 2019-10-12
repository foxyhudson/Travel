<template>
    <div>
      <div class="banner" @click="handleBennerClick">
        <img clas="banner-img" :src="bannerImg">
        <div class="banner-info">
          <div class="banner-title">{{sightName}}</div>
          <div class="banner-number">
            <span class="iconfont icontupian banner-icon" ></span>
            {{gallaryImgs.length}}
          </div>
        </div>
      </div>
      <fade-animation>
        <common-gallary
          @close = "handleGallaryClose"
          :imgs="gallaryImgs" v-show="showGallary">

        </common-gallary>
      </fade-animation>
    </div>
</template>

<script>
    import CommonGallary from 'common/gallary/Gallary'
    import FadeAnimation from 'common/fade/fade'
    export default {
        name: "DetailBanner",
        props:{
          sightName:String,
          bannerImg:String,
          gallaryImgs:Array
        },
        components:{
          CommonGallary,
          FadeAnimation
          },
        data(){
          return{
            showGallary:false,

          }
        },
        methods:{
          handleBennerClick(){
            this.showGallary=true
          },
          handleGallaryClose(){ //关闭画廊
            this.showGallary = false
          }
        }
    }
</script>

<style lang="stylus" scoped>
  .banner  //防抖动
    overflow:hidden
    height: 0
    padding-bottom : 55%
    position: relative
    .banner-img
      width: 100%
    .banner-info
      display: flex
      position: absolute
      left:0
      right: 0
      bottom: 0
      line-height: .6rem
      color: #fff
      background-image: linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,.8)) //渐变
      .banner-title
        flex:1
        font-size: .32rem
        padding : 0 .2rem
      .banner-number
        margin-top: .14rem
        padding: 0 .4rem
        line-height: .32rem
        height: .32rem
        border-radius: .2rem
        background: rgba(0,0,0,.8)
        font-size: .24rem
        .banner-icon
          font-size: .24rem
</style>
