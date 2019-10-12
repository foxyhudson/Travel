<template>
  <div class="container" @click="handleGallaryClick">
    <div class="wrapper">
      <swiper :options="swiperOptions">
        <swiper-slide class="juzhong" v-for="(item,index) of imgs" :key="imgs.index">
<!--          <img class="gallary-img" src="http://img1.qunarzz.com/sight/p0/1804/1a/1a48cc20b0d6ed44a3.img.jpg_r_800x800_9b21ceda.jpg" />-->
          <img class="gallary-img" :src="item" />
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
    export default {
        name: "CommonGallary",
        props:{
          imgs:{ //组件需要从外面拿图片
            type:Array,
            default (){ //默认值
              return [] //默认图片
            }
          }
        },
        methods:{
          handleGallaryClick(){
            this.$emit('close')
          }
        },
        data(){
          return{
            swiperOptions:{
              pagination:'.swiper-pagination',
              paginationType: 'fraction', //页码
              observeParents: true,   //监听到dom变化 自我刷新 不然页面进来展示可能由于宽度会出现异常
              observer:true           //监听到dom变化 自我刷新 不然页面进来展示可能由于宽度会出现异常
        }
          }
        }
    }
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container  //默认hidden所以要越界改
      overflow: inherit

  .container
    display: flex
    flex-direction: column
    justify-content: center
    z-index: 99
    position: fixed
    left: 0
    right: 0
    top: 0
    bottom: 0
    background: #000
    .wrapper
      height: 0
      width: 100%
      padding-bottom: 100%
      .gallary-img
        width: 100%
      .swiper-pagination
        color: #fff
        bottom: -1rem

</style>
