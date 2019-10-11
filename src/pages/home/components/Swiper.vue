<template>
  <div class="wrapper">
    <swiper :options="swiperOption" ref="mySwiper" >
      <!-- slides -->
      <swiper-slide v-for="item of swiperList" :key="item.id">
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
              imgUrl:'https://sk.5173cdn.com/sk_4/data/201909/00/C1/SwKowF2RUGAAAAAAAAgpIw5PJ8088.png'
            }]
          }
        }
    }
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background: #fff

  .wrapper
    overflow: hidden
    width: 100%
    height: 0
    padding-bottom: 31.25%
    background: #eee
    .swiper-img
      width: 100%
      height : 2.6rem


</style>
