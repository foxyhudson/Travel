<template>
  <div class="wrapper">
    <swiper :options="swiperOption" ref="mySwiper" >
      <!-- slides -->
      <swiper-slide v-for="item of swiperList" key="item.id">
        <img class="swiper-img" :src="item.imgUrl" />
      </swiper-slide>

      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
    export default {
        name: "HomeSwiper",
        data () {
          return{
            swiperOption:{
              pagination:'.swiper-pagination',
              loop: true
            },
            swiperList:[{
              id:'0001',
              imgUrl:'https://i0.hdslb.com/bfs/sycp/creative_img/201910/723f2b2ed088fa894e864b1bad13de32.jpg@1100w_484h_1c_100q.jpg'
            },
            {
              id:'0002',
              imgUrl:'https://img1.5173.com//e535e2aead824a4d8539b6edda7c3db1.jpg'
            }]
          }
        }
    }
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background: #fff
  .wrapper
    width:100%
    height:31.25vw
    background:#ccc
    .swiper-img
      width:100%
      height :3.5rem
      overflow hidden
</style>
