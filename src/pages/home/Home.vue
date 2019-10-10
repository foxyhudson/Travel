<template>
    <div>
      <home-header></home-header>
      <home-swiper></home-swiper>
    </div>
</template>

<script>
    import HomeHeader from './components/Header'
    import HomeSwiper from './components/Swiper'
    // import HomeSwiper from './components/Swiper'
    //引入组件
    export default {
        name: "Home",
        components:{
          HomeHeader,
          HomeSwiper
        }
    }
</script>

<style lang="stylus" scoped>

</style>
