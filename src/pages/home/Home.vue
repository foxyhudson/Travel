<template>
    <div>
      <home-header></home-header>
      <home-swiper></home-swiper>
      <home-icons></home-icons>
    </div>
</template>

<script>
    import HomeHeader from './components/Header'
    import HomeSwiper from './components/Swiper'
    import HomeIcons from './components/icons'
    // import HomeSwiper from './components/Swiper'
    //引入组件
    export default {
        name: "Home",
        components:{
          HomeHeader,
          HomeSwiper,
          HomeIcons
        }
    }
</script>

<style lang="stylus" scoped>

</style>
