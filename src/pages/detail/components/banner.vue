<template>
    <div>
      <div class="banner" @click="handleBennerClick">
        <img clas="banner-img" src="//img1.qunarzz.com/sight/p0/1804/1a/1a48cc20b0d6ed44a3.img.jpg_600x330_3f524da7.jpg" alt="">
        <div class="banner-info">
          <div class="banner-title">奥林匹克塔</div>
          <div class="banner-number">
            <span class="iconfont icontupian banner-icon" ></span>
            8
          </div>
        </div>
      </div>
      <common-gallary
        @close = "handleGallaryClose"
        :imgs="imgs" v-show="showGallary"></common-gallary>
    </div>
</template>

<script>
    import CommonGallary from 'common/gallary/Gallary'
    export default {
        name: "DetailBanner",
        components:{
          CommonGallary
          },
        data(){
          return{
            showGallary:false,
            imgs:['http://img1.qunarzz.com/sight/p0/1804/5f/5f59c2661add425aa3.img.jpg_r_800x800_ff390240.jpg',
                  'http://img1.qunarzz.com/sight/p0/1804/b6/b68ccb778c685283a3.img.jpg_r_800x800_da0c0853.jpg'
            ]
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
