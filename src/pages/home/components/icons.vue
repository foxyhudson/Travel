<template>
    <div class="icons">
      <swiper :options="swiperOption" v-if="showIcons">
        <swiper-slide v-for="(page,index) of pages" :key="index">
          <div class="icon"  v-for="item of pages[index]" :key="item.id">
            <div class="icon-img">
              <img class="icon-imgcontent" :src="item.imgUrl" alt="">
            </div>
            <p class="icon-desc">{{item.desc}}</p>
          </div>
        </swiper-slide>
      </swiper>
    </div>
</template>

<script>
    export default {
        name: "HomeIcons",
        props:{
          iconList:Array
        },
        data () {
          return{
            swiperOption:{
              autoplay:false
            }
          }
        },
      computed:{
          showIcons(){
            return this.iconList.length
          },
          pages () {
            const pages = []
            this.iconList.forEach((item,index)=>{
              const page = Math.floor(index / 8)
              if(!pages[page]){
                pages[page] = []
              }
              pages[page].push(item)
            })
            return pages
          }
      }
    }
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  @import "~styles/mixins.styl"
  .icons >>> .swiper-container

    height: 0
    padding-bottom: 50%
  .icons
    margin-top: .1rem
    .icon
      position: relative
      float: left
      width: 25%
      height: 0
      padding-bottom: 25%

      .icon-img
        position:absolute
        top:0
        right:0
        left:0
        bottom: .44rem
        box-sizing: border-box
        padding: .1rem

        .icon-imgcontent
          display: block
          margin: 0 auto
          height: 100%
      .icon-desc
        position : absolute
        left: 0
        right: 0
        bottom:0
        height: .44rem
        line-height: .44rem
        text-align: center
        color: $darkTestColor
        ellipsis()

</style>
